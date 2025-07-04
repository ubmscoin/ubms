# **백서** UBMS  
**작성일:** 2024-11-26  
**버전:** 1.51

---

## **목차**
1. 홍보  
   1.1. 진화적 개발  
   1.2. 독립적 코드베이스  
   1.3. 시대적 배경  
   1.4. 방향  
2. 기술 개요  
3. 경제 모델  
   3.1. 인센티브   
   3.2. 채굴 종류  
       3.2.1. POW 작업증명 채굴  
           3.2.1.1. 초반 채굴 설정  
           3.2.1.2. 후반 채굴 설정  
           3.2.1.3. 비트코인과 비교  
           3.2.1.4. 채굴 설정 결론  
       3.2.2. POS 지분증명 채굴  
       3.2.3. POB 행위증명 채굴  
   3.3. 수수료  
       3.3.1. 경제팩터  
       3.3.2. 혼잡팩터  
       3.3.3. 외부변수,내부상수  
       3.3.4. 수수료  
       3.3.5. 비트코인과 이더리움의 수수료 비교  
4. 네트워크 구조   
   4.1. UBMS의 혼잡방지 기술 PSAN (Role-Polymorphic Self-Adjusting Network) 소개  
   4.2. 청사진 (blueprint) 개념  
   4.3. UBMS 독자적 방식 주요 단계  
   4.4. 노드 수별 blueprint 예시  
   4.5. 이더리움 PoS와의 비교 – 노드 수별 테이블  
       4.5.1. 노드 수: 100개  
       4.5.2. 노드 수: 1,000개  
       4.5.3. 노드 수: 10,000개  
       4.5.4. 노드 수: 100,000개
5. UBMS 독창적 기술 특징  
   5.1. 완전 독립적 코드베이스  
   5.2. 합의 알고리즘  
   5.3. 스마트 계약 대체 기술  
   5.4. 역할다형성 자가조정 네트워크  
   5.5. UTXO 기반 메타데이터 스마트 컨트랙트  
       5.5.1. RGB 프로토콜 vs. 카르다노(eUTXO) vs. UBMS 비교  
   5.6. 독자기술 직렬화  
       5.6.1. 직렬화 성능 및 특성 비교  
       5.6.2. 평균 처리 시간   
   5.7 완전 분산형 구조   
       5.7.1 비콘체인(Beacon Chain)이 없다   
6. 가운영(준운영) 정의  
7. 블록체인 위기 대응 매뉴얼  
8. 참여자 위험 고지 (면책조항)   
9. 로드맵
    

---

## **1. 홍보**

### **1.1. 진화적 개발**

UBMS 프로젝트는 학습을 목적으로 시작한 프로젝트로 ,진화적 발전 모델을 기반으로 설계되었습니다.  
단계별 개발과 지속적인 개선 및 기능 추가를 목표로 하며, 끊임없이 발전하는 블록체인을 지향합니다.  
초기 버전은 블록체인의 기본적인 형태로 출시되나, 지속적인 업데이트를 통해 점진적으로 발전할 예정입니다.  
사용자에게는 초기에 다소 제한적인 기능만 제공되나, 이는 안정적인 시스템으로 나아가기 위한 필수적인 과정입니다.  
UBMS는 블록체인을 장기프로젝트로 삼아 "꾸준함이 승자의 유일한 전술이다"라는 철학에 따라 지속적인 개선을 약속합니다.

### **1.2. 독립적 코드베이스**

UBMS는 자체 개발 블록체인으로, 서드파티 라이브러리와 개인 창작 코드를 활용하여 개발됩니다.  
타 코인을 복사하거나 포크하지 않고 스스로 생산한 코드로 전체 프로젝트를 완전히 통제하며,  
기존 레거시코드와 커플링이 없기에 모든 코드조각을 자유롭게 가공할수 있고, 외부기술 종속에서 자유롭습니다.  
도전적 시도와 다양한 개량을 달성하기 위한 기술적 토대를 마련하는데 의의를 두고있습니다.  
상기의 이유로 코드비용을 최소화할수 있어 장차 개량과 확장에 유리합니다.

### **1.3. 시대적 배경**

블록체인은 이미 학문 및 교육 커리큘럼에 포함된 레거시 기술로 자리잡았으며,  
금융 산업 및 다양한 산업 분야에서 중요한 역할을 수행합니다.  
세계 각국은 연구 및 개발에 막대한 자금을 투입하나, 생각보다 느린 기술 발전 속도와 기본 아이디어에서 뚜렷한 진보가 없어, 여전히 도전할 이유로 충분합니다.

### **1.4. 방향**

UBMS(UTXO-Based Metadata Smart Contract)는 기존 비트코인의 한계를 극복하기 위한 독창적인 기술적 접근을 시도합니다.  
열정과 의지를 바탕으로, 시대의 필요에 부합하는 기술을 지속적으로 개발하겠습니다.

---

## **2. 기술 개요**

| 구성 요소            | 기술 내용                                                                 |
|---------------------|--------------------------------------------------------------------------|
| 합의 메커니즘       | PoW + PoS + PoB 통합 하이브리드 시스템                                     |
| 네트워크 구조       | PSAN: 역할다형성 자가조정 네트워크, 임계값 기반 릴레이·투표자 계산             |
| 합의 메시지 최적화  | 릴레이·투표자 수를 로그함수 기반으로 설정하여 메시지 수 최소화 (Data Storming 억제) |
| 전파 구조           | TTL=5, XOR 모듈러2 기반 피어 거리 계산, 효율적 Gossip 설계                  |
| 채굴 구조           | 초기 채굴 존재, 반감기 720블록, PoW → PoS 전환 기반 구조              |
| 인센티브  구조      | 채굴자 5%, 지분 보유자 95% 온체인 자동  (스테이킹 기반 PoS 인센티브)          |
| 행위증명 시스템     | POB: 5단계 디스트리뷰터 수수료 , 전송 트리 구조로 인센티브 자동 계산·기록        |
| 수수료 정책         | 시장가 기반 경제팩터 + 혼잡도 기반 혼잡팩터 × 기준수수료 공식 적용             |
| 스마트 컨트랙트     | UTXO 기반 페이로드 확장 구조, 조건문, TTL, 조건 실행 지원                        |
| 컨트랙트 비교 설계  | RGB/eUTXO 대비 온체인/오프체인 혼합 실행, 데이터 수정성, TTL, 조건 실행 지원       |
| 직렬화 방식         | 템플릿 기반 고속 직렬화, 구조체 공용체 기반 메모리 직접 복사 방식                 |
| 직렬화 성능         | 평균 처리 시간 0.15ms, FlatBuffers/ProtoBuf 대비 최소 오버헤드 구현              |
| 분산성 구조         | 비콘체인 없는 완전 분산 구조, 릴레이·투표자가 전담, 단일 실패점 제거               |
| 노드 최소 구성      | 릴레이 3, 투표자 5, 채굴자 1 → 최소 9노드로 완전한 합의 가능                      |
| 청사진 시스템       | log₂(N) 기반 BP 계산식으로 노드 수 증감에 따라 네트워크 자동 조정                |
| 미래 확장성         | DSCB(Dynamic Self-Computing Block) 기반 스마트 계약 예정                   |


UBMS는 위와 같은 독창적 기술들을 바탕으로,  
**자율적이고 합리적인 블록체인 생태계를 장기적으로 실현하는 것을 목표**로 합니다.

---

## **3. 경제 모델**

### **3.1. 인센티브  규칙**

UBMS의 채굴 인센티브는 채굴자의 기여도와 참여자의 지분에 따라 공정하게 처리됩니다.

---

### **3.2. 채굴 종류**

#### **3.2.1. POW 작업증명 채굴**
- **깃허브 소스공개 이후에는 누구나 POW채굴에 참여할수 있습니다.**


##### **3.2.1.1 초반 채굴 설정**

**작업증명 채굴은 지분증명 채굴과 일정 비율로 나누게 됩니다. 아래는 채굴 총량을 기준으로 계산합니다.**

**기본 계산**  
- **채굴 기간:** 6시간 = # $$6 \times 60 \times 60 = 21{,}600 \,\text{초}$$  
- **블록 생성 시간:** 10초/block  
- **총 블록 수:**  
  # $$\frac{21{,}600}{10} = 2{,}160 \,\text{블록}$$  

**반감기 간격 및 인센티브 설정**  
- **반감기 간격:** 540블록 (블록 생성 간격 10초 가정)  
- **초기 인센티브 $$R_0$$:** 1,000 UBMS/block  
- **반감기 횟수:** 4회  

**초기 채굴 단계 요약**  
- **구간별 인센티브:**  
  1) 1구간:  $$R_0 = 1{,}000$$ UBMS/block  
  2) 2구간:  $$\tfrac{R_0}{2} = 500$$ UBMS/block  
  3) 3구간:  $$\tfrac{R_0}{4} = 250$$ UBMS/block  
  4) 4구간:  $$\tfrac{R_0}{8} = 125$$ UBMS/block  

- **구간별 블록 수:** 540블록씩 (총 2,160블록)  
- **구간별 채굴량 $$C_{1,i}$$:**  
  1) ## $$C_{1,1} = 1{,}000 \times 540 = 540{,}000$$  
  2) ## $$C_{1,2} = 500 \times 540 = 270{,}000$$  
  3) ## $$C_{1,3} = 250 \times 540 = 135{,}000$$  
  4) ## $$C_{1,4} = 125 \times 540 =  67{,}500$$  

- **총 채굴 코인 수 $$C_1$$:**  
  # $$C_1 = \sum_{i=1}^{4} C_{1,i}  = 1{,}012{,}500 \,\text{UBMS}$$  

---

##### **3.2.1.2 후반 채굴 설정**

**기본 계산**  
- **반감기 간격:** 4년  
- **블록 생성 시간:** 10분/block  
- **연간 블록 수:**  
  ## $$\frac{365 \times 24 \times 60}{10} = 52{,}560 \,\text{블록/년}$$  
- **반감기 간격 블록 수 $$H'$$:**  
  ## $$4 \times 52{,}560 = 210{,}240 \,\text{블록}$$  

**후반 채굴 단계 요약**  
- **후반 초기 인센티브 $$R_0'$$:** 48 UBMS/block  
- **반감기 횟수:** 5회  
- **구간별 인센티브:**  
  1) 5구간:  $$R_0' = 48$$ UBMS/block  
  2) 6구간:  $$\tfrac{R_0'}{2} = 24$$ UBMS/block  
  3) 7구간:  $$\tfrac{R_0'}{4} = 12$$ UBMS/block  
  4) 8구간:  $$\tfrac{R_0'}{8} = 6$$ UBMS/block  
  5) 9구간:  $$\tfrac{R_0'}{16} = 3$$ UBMS/block  

- **구간별 블록 수:** 210,240블록씩 (총 1,051,200블록)  
- **구간별 채굴량 $$C_{2,j}$$:**  
  1) ## $$C_{2,5} = 48 \times 210{,}240 = 10{,}091{,}520$$  
  2) ## $$C_{2,6} = 24 \times 210{,}240 = 5{,}045{,}760$$  
  3) ## $$C_{2,7} = 12 \times 210{,}240 = 2{,}522{,}880$$  
  4) ## $$C_{2,8} = 6 \times 210{,}240 = 1{,}261{,}440$$  
  5) ## $$C_{2,9} = 3 \times 210{,}240 = 630{,}720$$  
  6) ## $$C_{2,10} = 1.5 \times 210{,}240 = 315{,}360$$  
  7) ## $$C_{2,11} = 0.629032 \times 210{,}240 \approx 132{,}320$$  

- **총 채굴 코인 수 $$C_2$$:**  
  # $$C_2 = \sum_{j=5}^{11} C_{2,j} = 20{,}000{,}000 \,\text{UBMS}$$  
---

##### **3.2.1.3 비트코인과 비교**

**비트코인의 채굴 구조**  
1. **블록 생성 시간:** 10분/block  
2. **반감기 간격:** 210,000블록 (약 4년)  
3. **초기 인센티브:** 50 BTC/block  
4. **총 공급량:** 21,000,000 BTC  

**반감기 간격 및 인센티브 비교**

| **구분**           | **비트코인**                   | **UBMS**                                                                 |
|--------------------|--------------------------------|--------------------------------------------------------------------------|
| 반감기 간격        | 210,000블록 (약 4년)           | 210,240블록 (4년, 10분/블록 가정)                                        |
| 초기 인센티브          | 50 BTC/block                   | 48 UBMS/block (후반 초기 인센티브)                                          |
| 총 공급량          | 21,000,000 BTC                 | **21,000,000 UBMS** (#초반 1,012,500 + 후반 20,000,000 = 21,012,500 (대략)) |

---

##### **3.2.1.4 채굴 설정 결론**

| **단계**      | **총 채굴 코인 수**   | **총 블록 수**    | **반감기 간격**               | **초기 인센티브**         | **반감기 횟수** |
|---------------|----------------------|-------------------|-----------------------------|-----------------------|-----------------|
| 초반 채굴     | 1,012,500개          | 2,160블록         | 540블록 (블록 생성 간격 10초) | 1,000 UBMS/블록       | 4회             |
| 후반 채굴     | 19,552,320개         | 1,051,200블록     | 210,240블록 (4년, 10분/블록)  | 48 UBMS/블록          | 5회             |

---

| **구분**   | **반감기 번호** | **블록당 인센티브 (UBMS)** | **단계 총 채굴량 (UBMS)**    | **블록 높이**               | **누적 채굴량 (UBMS)**       |
| --------- | ------------- | -------------------- | ------------------------ | ------------------------- | --------------------------- |
| 초반 채굴 | 1             | 1,000                | 540,000                  | 0 ~ 539                   | 540,000                     |
| 초반 채굴 | 2             | 500                  | 270,000                  | 540 ~ 1,079               | 810,000                     |
| 초반 채굴 | 3             | 250                  | 135,000                  | 1,080 ~ 1,619             | 945,000                     |
| 초반 채굴 | 4             | 125                  | 67,500                   | 1,620 ~ 2,159             | 1,012,500                   |
| 후반 채굴 | 5             | 48                   | 10,091,520               | 2,160 ~ 212,399           | 11,104,020                  |
| 후반 채굴 | 6             | 24                   | 5,045,760                | 212,400 ~ 422,639         | 16,149,780                  |
| 후반 채굴 | 7             | 12                   | 2,522,880                | 422,640 ~ 632,879         | 18,672,660                  |
| 후반 채굴 | 8             | 6                    | 1,261,440                | 632,880 ~ 843,119         | 19,934,100                  |
| 후반 채굴 | 9             | 3                    | 630,720                  | 843,120 ~ 1,053,359       | 20,564,820                  |
| 후반 채굴 | 10            | 1.5                  | 315,360                  | 1,053,360 ~ 1,263,599     | 20,880,180                  |
| 후반 채굴 | 11            | 0.75                 | 157,680                  | 1,263,600 ~ 1,473,839     | 21,037,860                  |


---

| **구간 번호** | **블록 높이 시작** | **블록 높이 끝** | **블록 개수**          |
| :----------: | :---------------: | :-------------: | :---------------------: |
| 1구간        | 0                 | 539             | 539 − 0 + 1 = 540개     |
| 2구간        | 540               | 1,079           | 1,079 − 540 + 1 = 540개 |
| 3구간        | 1,080             | 1,619           | 1,619 − 1,080 + 1 = 540개 |
| 4구간        | 1,620             | 2,159           | 2,159 − 1,620 + 1 = 540개 |

---

| **구간 번호** | **블록 높이 시작** |  **블록 높이 끝**  | **블록 개수**            |
| :----------: | :---------------: | :--------------: | :-----------------------: |
| 5구간        | 2,160             | 212,399          | 212,399 − 2,160 + 1 = 210,240개 |
| 6구간        | 212,400           | 422,639          | 422,639 − 212,400 + 1 = 210,240개 |
| 7구간        | 422,640           | 632,879          | 632,879 − 422,640 + 1 = 210,240개 |
| 8구간        | 632,880           | 843,119          | 843,119 − 632,880 + 1 = 210,240개 |
| 9구간        | 843,120           | 1,053,359        |1,053,359 − 843,120 + 1 = 210,240개   |

---

### **3.2.2. POS 지분증명 채굴**

UBMS의 POS 채굴은 온체인 방식으로 **모든 스테이킹 과정이 블록체인에 기록**되며,  
UBMS SCAN을 통해 **누구나 투명하게 확인**할 수 있습니다.  

기존의 단순 비례 대신, UBMS는 **Shifted Sigmoid 함수 기반의 알고리즘**을 도입하였습니다.  
이 방식은 고지분 참여자의 과도한 독점을 방지하도록 **비선형적 곡선 보정**을 적용합니다.

---

### **인센티브 공식**

- 채굴자 인센티브 (PoW): 전체 인센티브의 5%
- 스테이커 인센티브 (PoS): 전체 인센티브의 95%

스테이커 개별 인센티브는 다음과 같이 계산됩니다.

#### **Sigmoid 가중치 계산**

# $$R(x) = \frac{1}{1 + e^{-z}}$$
# $$z = \left( \frac{x + s}{T} - 0.5 \right) \times 10$$

- $$\ R \$$ : 시그모이드
- $$\ z \$$ : 입력값으로 이곳을 조정해 시프트시킨다. 
- $$\ x \$$ : 스테이커의 지분 수량  
- $$\ T \$$ : 전체 스테이커 지분 총합
- $$\ r = 0.2 \$$ : 좌측시프 비율  
- $$\ s = T \times r \$$ : 시프트값
- 10을 곱한것은 은 소지분자와 대지분자의 차이를 뚜렷하게 하여 유의미한 차이를 만든다



이로부터 나온 각 참여자의 \( R(x) \) 값을 **전체 합으로 정규화**하여 사용합니다.

---

### **예시 시뮬레이션**

- 총 인센티브: **100 UBMS**
- 채굴자 인센티브 (5%): **5 UBMS**
- 스테이커 대상 인센티브 (95%): **95 UBMS**
- 전체 지분 합: **10,000**


# $$\text{지분당 인센티브}(x) = 95 \times \frac{R(x)}{\sum_{i=1}^{n} R(x_i)} $$
# $$\text{입력값 셋팅} = \left( \frac{x + (T \times 0.2)}{T} - 0.5 \right) \times 10$$
여기서,  
- $$\ T = 10,000 \$$ : 전체 스테이커 지분 총합  
- 시프트 값 $$\ s = T \times 0.2 = 2,000 \$$


#### **지분자별 결과 (Sigmoid 적용)**

| 참여자 | 지분 수량 |  비율 (%) | 인센티브 (UBMS) |
|--------|-----------|----------------|--------------|
| A      | 100       | 2.25%          | 2.14         |
| B      | 200       | 4.04%          | 3.83         |
| C      | 300       | 6.01%          | 5.71         |
| D      | 500       | 8.89%          | 8.45         |
| E      | 800       | 12.23%         | 11.62        |
| F      | 1,300     | 15.13%         | 14.37        |
| G      | 1,600     | 16.48%         | 15.66        |
| H      | 1,800     | 16.64%         | 15.81        |
| I      | 1,900     | 16.48%         | 15.66        |
| J      | 1,500     | 12.37%         | 11.75        |
| **합계** | **10,000** | **100%**         | **95.00**     |

---

### **UBMS 인센티브 알고리즘의 장점**

- **대지분 독식 방지**  
  인센티브는 선형이 아닌 곡선화되어 고지분자가 급격히 독식하지 못함

- **소지분 참여자 보정**  
  적은 지분도 의미 있는 인센티브을 획득 가능 → **지속적 참여 유도**

- **수학적으로 정당함**  
  시프트된 Sigmoid는 정규화 이후에도 항상 전체 인센티브 총합을 유지함

---

### **요약**

UBMS의 POS 인센티브 시스템은  
- **총 인센티브의 5%는 채굴자에게**,  
- **95%는 Sigmoid 가중치를 통해 비선형 형태가**되며,  

이는 지분 참여가 **불균형하거나 극단적인 경우에도 안정적이고 공정한 인센티브 구조**를 제공합니다.


---

#### **3.2.3. POB 행위증명 채굴** 

POB 행위증명 채굴은 사용자가 코인을 전송할 때 발생하는 수수료(fee)를, 네트워크 확장에 기여한 사람들에게 인센티브를 제공하는 온체인 방식의 채굴입니다.  
행위증명의 인센티브는 블럭에 기록되고 UBMS 시스템이 수행하기에 누락이 없고 행위의 인센티브을 장담합니다.  
여기서 **디스트리뷰터**란 UBMS 네트워크 실제적인 확장에 기여한 사용자의 지갑 주소를 의미하며, 이 주소가 반드시 입력되어야만 UBMS 코인이 올바르게 작동합니다.

## 수수료 인센티브 원리

거래 전송 시 발생하는 수수료는 최대 5단계까지 자동관리됩니다.  
각 단계별 인센티브 비율은 아래와 같이 정해집니다.

- **1대 (가장 최근에 디스트리뷰트한 사람):** 60%  
- **2대:** 20%  
- **3대:** 10%  
- **4대:** 7%  
- **5대 (가장 오래된 디스트리뷰터):** 3%

즉, 전체 수수료 금액을 \( F \)라 할 때, 각 디스트리뷰터에게 지급되는 인센티브는 다음 식으로 계산됩니다.

예를 들어, 거래 전송 시 수수료가 1,000원일 경우, 각 디스트리뷰터에게 지급되는 금액은 다음과 같이 계산됩니다.

| 단계  | 인센티브 비율 | 인센티브 금액 (원)      |  
|-------|-----------|---------------------|  
| 1대   | 60%       | 1,000 × 0.60 = 600  |  
| 2대   | 20%       | 1,000 × 0.20 = 200  |  
| 3대   | 10%       | 1,000 × 0.10 = 100  |  
| 4대   | 7%        | 1,000 × 0.07 = 70   |  
| 5대   | 3%        | 1,000 × 0.03 = 30   |

이와 같이 인센티브는 각 단계별로 고정된 비율에 따라 나누어 지급되며, 디스트리뷰터들의 인센티브가 이루어집니다.

## 디스트리뷰터 관리 및 필수 입력

- UBMS 코인의 정상 작동을 위해서는 반드시 거래 시 **디스트리뷰터**의 지갑 주소가 입력되어야 합니다.  
- 거래를 전송하는 사용자가 확산에 기여한 사람의 주소 목록을 입력할 경우, 이 목록은 역순으로 정렬되어 가장 최근에 기여한 사람이 1대(60%)에 해당하며, 그 이후 순서대로 2대, 3대, 4대, 5대의 인센티브 비율이 적용됩니다.

이와 같은 구조는 사용자들이 노력을 통해 확장하고, 그에 따른 수수료 인센티브을 통해 네트워크의 활성화 및 확산에 기여하도록 설계되었습니다.  
아래는 UBMS 네트워크에서 디스트리뷰터의 자식 주소가 계층적으로 연결된 구조를 트리로 나타낸 예시입니다.

```
18eAuVSXcQ5Gdz6GVCd611TtwAxmhD5dXW  (level 0)
├── 1Aj4YWxVi9rbKnnDN9T6dohVcfSxqBJ2JD  (level 1)
│   ├── 1GqZ5QuLQe5YxDFyLBcDkPn9hpLX7dGge2  (level 2)
│   └── 1HgQt3TfcQz9xz1bDNZDnVSmM1d99FQ2pb  (level 2)
│       ├── 1JmLNR1dY65kZJACbzyKqu2SGnTpM1bZPx  (level 3)
│       │   ├── 1MMMAsyH3qLFFcex3uJ2qAjSDCzu4qobv5  (level 4)
│       │   │   ├── 1PgpaijEyheTQ2DdzK25Kosm2awWtzcHdK  (level 5)
│       │   │   ├── 1PqjsiCuQjhGJaDky2s35H4P7dGfQ3uoaM  (level 5)
│       │   │   └── 1U25D13kfGUGDScQ8uVg7kjqcdHtYSFCh  (level 5)
│       │   ├── 1NQ4GMcxZQjFUPB7Ahej4XUsMWoLy7Uu33  (level 4)
│       │   └── 1NUPTVBfuk6fjt21cqPoKA3HT7gDaXLCUi  (level 4)
│       └── 1Jyh4WjUgQ4HL4WjbtTuR6jviw2SMixErT  (level 3)
└── 1BhpGXNKTQhuJsWAGS8PGudx11FrRLz6n6  (level 1)
```

- **POB 관련 오픈베타테스트를 통해 얻은 교훈으로 POB유지가 트래픽유발이 심각하여 시스템이 감당할수 없는경우 예고없이 패치를 통해 중단될 수 있습니다.**

---

#### **3.3.2. 혼잡팩터**

혼잡팩터는 최근 250개 블록의 네트워크 혼잡도를 측정하여 산출됩니다.  
네트워크에 대기 중인 거래 수를 기반으로 하며, 혼잡도가 높을 경우 혼잡팩터 $$CF$$는 1.0보다 큰 값으로 조정됩니다.  
이를 통해 네트워크 혼잡 상황에서는 추가 수수료를 인상하여 스팸 트랜잭션을 방지하고,  
네트워크의 안정성을 확보할 수 있도록 설계되어 있습니다.

---

#### **3.3.3. 외부변수**

항상 부정확한 경제팩터를 얻기 위해 트랜잭션을 조사하여 시장가를 추론할 필요가 없습니다.  
우리가 알고 싶은 시장가는 시스템 밖의 코인마켓캡과 같은 가격공시 사이트로부터 수신되는 외부정보를 참고합니다.  
이 변수값은 1 UBMS당 시장가의 기준 가격을 제공하며, 기저 수수료 산출에 필수적입니다.  
기존 업체들은 내부 계산 방식에만 의존하다 보니 비현실적인 높은 수수료 정책을 적용하는 경우가 많으나,  
UBMS는 외부 데이터를 활용하여 보다 현실적이고 합리적인 수수료 정책을 구현합니다.  
* 개발 시점인 지금은 유통될 수 없어 외부에서 시장가를 얻을 수 없기에, 내부상수 액면가만 적용합니다.  
* 장차 외부에서 UBMS의 값을 공시하는 곳이 생기거나 거래소에 상장하게 되면 실현될 부분입니다.


---

#### **3.3.4. 수수료 계산**

외부에서 수신한 1 UBMS의 시장가를 기준으로 기저 수수료가 결정됩니다.  
1 UBMS당 내부 상수를 **10,000원**으로 설정하고, 이에 해당하는 기저 수수료는 **1,000원**으로 정합니다.  
시장에서 고평가되어 1 UBMS당 시장가가 **100,000,000원**에 달할 경우, 경제팩터의 효과로 최종 수수료는 **100,000원**이 됩니다.  
외부 데이터에서 변수값을 받아와 경제팩터를 산출하며,  
최근 250개 블록의 혼잡도를 반영한 네트워크 혼잡팩터를 곱하여 최종 수수료를 계산합니다.

- **기준 시장가:** $$v_0 = 10\,000 \, \text{원}$$  
- **기저 수수료:** $$B = 1000 \, \text{원}$$  
- **경제팩터:**  
 ## $$EF = \left(\frac{v}{v_0}\right)^{0.5} = \sqrt{\frac{v}{10\,000}}$$  
- **네트워크 혼잡팩터:** $$CF$$ (최근 250개 블록의 혼잡도를 반영; 기본값 $$CF = 1.0$$)

따라서 최종 수수료 $$F$$는 다음과 같이 계산됩니다.

# $$F = B \times EF \times CF = 1000 \times \sqrt{\frac{v}{10\,000}} \times CF$$

여기서,  
- **$$F$$:** 최종 수수료 (원 단위)  
- **$$v$$:** 1 UBMS의 시장가 (원 단위)

##### 예시 1: (시장가 $$v = 10\,000 \, \text{원}$$)
- $$EF = \sqrt{\frac{10\,000}{10\,000}} = \sqrt{1} = 1$$  
- $$CF = 1.0$$  
- $$F = 1000 \times 1 \times 1.0 = 1000 \, \text{원}$$

##### 예시 2: (시장가 $$v = 100\,000\,000 \, \text{원}$$)
- $$EF = \sqrt{\frac{100\,000\,000}{10\,000}} = \sqrt{10\,000} = 100$$  
- $$CF = 1.0$$  
- $$F = 1000 \times 100 \times 1.0 = 100\,000 \, \text{원}$$

아래 표는 외부에서 받아오는 시장가 $$v$$를 1,000원에서 100,000,000원까지 10배 단위로 증가시킬 때 계산된 최종 수수료 $$F$$를 보여줍니다 (혼잡팩터 $$CF = 1.0$$로 가정).

| 시장가 $$v$$ (원)      | $$\sqrt{\frac{v}{10\,000}}$$ 값      | 최종 수수료 $$F$$ (원)              |
|-----------------------|------------------------------------|-------------------------------------|
| 1,000                 | $$\sqrt{0.1} \approx 0.316$$         | $$1000 \times 0.316 \approx 316$$    |
| 10,000                | $$\sqrt{1} = 1$$                     | $$1000 \times 1 = 1000$$             |
| 100,000               | $$\sqrt{10} \approx 3.162$$          | $$1000 \times 3.162 \approx 3162$$   |
| 1,000,000             | $$\sqrt{100} = 10$$                  | $$1000 \times 10 = 10\,000$$         |
| 10,000,000            | $$\sqrt{1000} \approx 31.623$$       | $$1000 \times 31.623 \approx 31\,623$$|
| 100,000,000           | $$\sqrt{10\,000} = 100$$             | $$1000 \times 100 = 100\,000$$       |

---

#### **비트코인과 이더리움의 수수료**

- **비트코인**  
  비트코인의 수수료는 주로 트랜잭션의 바이트 크기와 네트워크의 혼잡도에 따라 결정됩니다.  
  예를 들어, 낮은 거래 금액에서도 네트워크 혼잡 시 몇 천 원에서 수 만 원대의 수수료가 발생할 수 있으며,  
  거래 금액과 무관하게 고정된 수준의 수수료가 부과되는 경향이 있습니다.

- **이더리움**  
  이더리움의 수수료는 가스 가격과 가스 사용량에 따라 결정됩니다.  
  복잡한 스마트 계약이나 네트워크 혼잡 시, 수수료는 몇 천 원에서 수 만 원, 때로는 그 이상이 될 수 있으며,  
  거래 금액과 비례하지 않고 트랜잭션의 복잡성과 네트워크 상황에 크게 좌우됩니다.

---

#### **비교**

- **낮은 거래 금액 (예: 1,000원 ~ 10,000원):**  
  UBMS 모델은 거래 금액이 매우 낮을 때 다소 높은 수수료 비율을 보일 수 있으나,  
  비트코인과 이더리움은 최소 수수료가 고정되거나 네트워크 혼잡에 따른 과도한 수수료로 인해 오히려 부담이 큽니다.

- **중간 거래 금액 (예: 100,000원 ~ 1,000,000원):**  
  UBMS는 거래 금액 증가에 따라 수수료 비율이 급격히 낮아져,  
  100,000원 거래 시 약 3.16%, 1,000,000원 거래 시 1%의 수수료를 부과합니다.  
  반면, 비트코인과 이더리움은 거래 금액과 무관하게 일정 수준의 수수료가 적용되어 상대적으로 비효율적입니다.

- **고액 거래 (예: 10,000,000원 ~ 100,000,000원):**  
  UBMS의 수수료는 10,000,000원 거래 시 약 0.316%, 100,000,000원 거래 시 0.1%로 매우 낮은 비율을 적용합니다.  
  이는 대량 거래 시 비용 부담을 크게 줄여주며,  
  비트코인과 이더리움은 거래 금액과 관계없이 일정한 절대 수수료가 부과되어 고액 거래에 불리합니다.

| 거래 금액 (원)   | 비트코인 수수료 (원)      | 이더리움 수수료 (원)       | UBMS 수수료 (원)            |
|------------------|--------------------------|--------------------------|-----------------------------|
| 1,000            | 약 3,000 ~ 5,000         | 약 3,000 ~ 5,000         | 약 316                      |
| 10,000           | 약 3,000 ~ 5,000         | 약 3,000 ~ 5,000         | 1,000                       |
| 100,000          | 약 5,000 ~ 7,000         | 약 5,000 ~ 7,000         | 약 3,162                    |
| 1,000,000        | 약 5,000 ~ 10,000        | 약 5,000 ~ 10,000        | 10,000                      |
| 10,000,000       | 약 10,000 ~ 15,000       | 약 10,000 ~ 15,000       | 약 31,623                   |
| 100,000,000      | 약 10,000 ~ 15,000       | 약 10,000 ~ 15,000       | 100,000                     |

도표는 비트코인과 이더리움 혼잡팩터 CF 1.0을 기준으로 네트워크 혼잡 시 10배까지 증액됩니다.  
송금 1,000원에 수수료 5,000원? 혼잡 시 10배 10,000 ~ 50,000 원?  
급격한 혼잡이나 특정 이벤트(예: 대규모 ICO, NFT 발매 등)가 발생하면, 심지어 1건당 수수료가 30,000원에서 수십만원 이상으로 급등하는 사례도 보고되고 있습니다.  
비트코인과 이더리움의 수수료가 불합리한 것은 네트워크 내부 트랜잭션을 모집단으로 EF를 산출하기 때문입니다.  
자유시장 경제에 의존하여 수요공급으로 가치가 결정되는 암호화폐가 화폐유통을 중계하거나 시장가치를 공시하는 거래소의 등장을 예측하지 못했을까요?  
개발자의 아집과 외부시장과 시스템과의 소통단절이 부른 대참사라고 할 수 있습니다.

---

### **3.3.5. 결론 (수수료 비교)**

UBMS의 수수료 공식은 외부에서 수신한 시장가와 내부상수로 결정된 기저 수수료 그리고, 경제팩터 및 최근 250개 블록의 혼잡도를 반영한 네트워크 혼잡팩터를 곱하여 최종 수수료를 산출합니다.  
따라서, 시장가가 낮은 경우 (1 UBMS당 10,000원 기준)에는 1,000원의 수수료가 적용되며,  
시장가가 높은 경우 (1 UBMS당 100,000,000원 기준)에는 100,000원의 수수료가 적용됩니다.  
특히, 중대형 거래에서는 매우 낮은 수수료 비율을 제공하여 거래 비용 부담을 크게 줄입니다.  
반면, 비트코인과 이더리움은 거래 금액과 무관하게 고정되거나 네트워크 혼잡에 따른 높은 수수료가 부과되어,  
낮은 거래에서는 부담이 크고 고액 거래에서는 비례성이 떨어지는 단점을 보입니다.  
이와 같이 UBMS의 수수료 정책은 현실적인 시장 상황과 네트워크 상태를 반영한 전략적인 수수료율을 제공함으로써,  
기존 방식보다 합리적입니다.

---

## **4. 네트워크 구조**  

### **4.1. UBMS의 혼잡방지 기술 PSAN (Role-Polymorphic Self-Adjusting Network) 소개**

- 미리계산된 청사진을 정적해법과 동적해법을 동시에 제안합니다.
- 메시지 폭증 방지, CF(혼잡 트래픽) 완화를 목표합니다.
- AI나 샤딩 기술은 현재 적용되지 않았으나, 노드가 늘면 확장 가능합니다.

### **4.2. 청사진 (blueprint) 개념**

- 네트워크 노드 수에 맞춰 blueprint함수(이하 BP)로 계산된 홀수 개의 릴레이 (relay)와 투표자 (voter)를 사용

### **4.3. UBMS 독자적 방식 주요 단계**
#### 이더리움과 비교하면 UBMS 네트워크는 비콘체인이 없고 구조적,절차적으로 단순하고 가볍습니다. 비트코인은 네트워크 구조가 달라 수평비교가 안되어 이하 도표에서 생략합니다.

1. **릴레이 (R) 및 투표자 (V) 선정 (BP함수 적용)**  
2. **투표를 통한 채굴자 (Miner) 선정**  
   - 투표자는 스테이크 기반 가중치로 투표  
   - 릴레이가 결과를 수합
3. **채굴자가 블록 생성 후 검증**  
   - 투표자들이 다수결로 블록 승인
4. **블록 전파 (gossip)**  
   - Miner → 투표자 → 전체 네트워크
5. **하트빗 시 CF 폭증 억제**  
   - 블록 업데이트 후 전체 노드가 하트빗, (UBMS 하트빗은 이더리움의 노드 디스커버리 기능을 겸 하고있어 효율적임)
6. **DHT로 롤백**  
   - 블록 해시가 다수와 다르면 인접 노드에서 롤백을 지원

### **4.4. 노드 수별 BP 예시**

#### 느린 성장률

UBMS gossip 프로토콜은 TTL이 5로 기본값 설정되 있으며, 한 번의 전파에서 최대 5개의 논리적으로 가까운 피어(lookup 결과)를 사용합니다.  
피어간의 거리계산은 모듈러2(XOR연산) 함수를 사용합니다.
네트워크 노드 수 $$N$$가 증가하면 전체 가능한 피어 수는 기하급수적으로 늘어나지만, 실제 필요한 릴레이와 투표자 수는 로그함수를 사용해 점진적으로 증가합니다.  
이는 네트워크 확장이 커지더라도 합의 과정에서 메시지 전파 부담을 급격하게 늘리지 않도록 해줍니다.

#### 최소 노드
최소 3개의 relay 노드 ,5개의 vote 노드가 존재해야 하고 추가로 1명의 채굴자가 있어야 하기에 네트워크에서 필요한 최소노드수는 9개입니다.

#### 홀수 유지

다수결 원칙을 명확히 하기 위해 항상 홀수로 설정합니다.  
홀수 릴레이와 투표자 수를 사용하면, 과반수 이상의 표를 쉽게 판별할 수 있고, 투표 및 검증에서 결정적인 결과를 도출할 수 있습니다.
아래식에서 바닥함수(floor function)가 사용된것은 max 함수가 실수값을 반환하는것을 방지하기 위해서입니다.

#### 최적의 속도 확보

UBMS gossip 방식에서는 한 번에 5개의 lookup 결과를 활용하여 메시지를 전파하고, TTL 5 내에서 빠른 동기화를 이루는 것이 목표입니다.  
기본값으로 gossip전파는 이론상 3125개의 노드에 도달할수 있습니다. 노드가 늘면 TTL 값을 늘려 전파 범위를 늘리면 됩니다.   
합의 단계에선 기본값 5개가 아닌 BP로 계산된 모든 수의 투표자를 대상으로 최초 전파하여 적은수의 TTL로 빠른 동기화를 달성하고 데이터 스토밍(Data Storming)을 방지합니다.   
만약 릴레이와 투표자 수가 과도하게 증가하면, 각 노드의 처리 부담이 커져 합의 지연이 발생할 수 있습니다.  
따라서 $$\log_2(N)$$에 기반해 R과 V를 서서히 증가시킴으로써, 네트워크 규모에 따라 최적의 속도를 유지할 수 있도록 조절하는 것입니다.


아래는 노드 수 $$(N)$$ 증가에 따라 릴레이 $$(R)$$ ·투표자 $$(V)$$를 설정하는 BP함수의 예시입니다.  
$$(\log_2(N))$$ 기반으로 서서히 늘립니다.

# $$R = \max\bigl(3, \lfloor \tfrac{\log_2(N)}{2} \rfloor \times 2 + 1\bigr)$$

# $$V = \max\bigl(5, \lfloor \tfrac{\log_2(N)}{1.2} \rfloor \times 2 + 1\bigr)$$

청사진값 예시:

- **100개 노드:**  
  $$\log_2(100) \approx 6.64$$  
  $$R \approx 3,\quad V \approx 11$$

- **1,000개 노드:**  
  $$\log_2(1000) \approx 9.96$$  
  $$R \approx 5,\quad V \approx 21$$

- **10,000개 노드:**  
  $$\log_2(10000) \approx 13.28$$  
  $$R \approx 7,\quad V \approx 51$$

- **100,000개 노드:**  
  $$\log_2(100000) \approx 16.61$$  
  $$R \approx 11,\quad V \approx 101$$

R, V 규모를 과도하게 키우지 않고, 필요할 때만 조금씩 늘려 메시지 폭발을 방지합니다.

### **4.5. 이더리움 PoS와의 비교 – 노드 수별 테이블**

#### **4.5.1. 노드 수: 100개**

| 항목           | UBMS                         | 이더리움 PoS            | 비고                         |
|----------------|-----------------------------|-------------------------|------------------------------|
| 릴레이/투표자  | R=3, V=11                   | 위원회 약 128명         | UBMS 선정 메시지 훨씬 적음    |
| 합의 메시지    | 투표(11×3=33), 검증(11), 하트빗(100) | 위원회 투표 128건+, gossip(100건+) | UBMS가 초기 합의에 필요한 메시지 적음 |
| CF(혼잡 트래픽)| 100노드 정도면 하트빗도 크지 않음  | 이더리움도 비슷하게 부담 적음  | 소규모에선 둘 다 빠르고 안정적  |

#### **4.5.2. 노드 수: 1,000개**

| 항목           | UBMS                             | 이더리움 PoS                   | 비고                          |
|----------------|---------------------------------|--------------------------------|-------------------------------|
| 릴레이/투표자  | R=5, V=21                       | 위원회 128~256명               | UBMS는 소수 릴레이, PoS는 위원회 증가  |
| 합의 메시지    | 투표(21×5=105), 검증(21), 하트빗(1,000) | 위원회 투표(128~256건+), gossip(1,000건+) | UBMS 합의가 단순·메시지 절약      |
| CF(혼잡 트래픽)| 하트빗 1,000건 발생하나 투표·검증은 간단  | PoS도 gossip 1,000건, 위원회가 커짐  | UBMS가 합의 속도가 빠름         |

#### **4.5.3. 노드 수: 10,000개**

| 항목           | UBMS                                             | 이더리움 PoS           | 비고                                          |
|----------------|-------------------------------------------------|------------------------|-----------------------------------------------|
| 릴레이/투표자  | R=7, V=51                                       | 위원회 약 512명         | UBMS는 소수 릴레이, PoS 위원회 512명            |
| 합의 메시지    | 투표(51×7=357), 검증(51), 하트빗(10,000)         | 위원회투표 512+, gossip 10,000+ | UBMS 초기 합의 적은 메시지, CF는 노드 수만큼 발생 |
| CF(혼잡 트래픽)| 하트빗 10,000건으로 혼잡 위험                    | PoS도 gossip 10,000건 이상  | 둘 다 대규모, UBMS 합의부담은 상대적 경량         |

#### **4.5.4. 노드 수: 100,000개**

| 항목           | UBMS                                              | 이더리움 PoS             | 비고                                            |
|----------------|---------------------------------------------------|--------------------------|-------------------------------------------------|
| 릴레이/투표자  | R=11, V=101                                       | 위원회 수천명 이상        | UBMS는 제한적 합의, PoS는 위원회가 기하급수적 증가  |
| 합의 메시지    | 투표(101×11=1,111), 검증(101), 하트빗(100,000)      | 수천~만건 위원회, gossip 100,000+ | UBMS 투표·검증은 적으나 하트빗이 100,000건 이상     |
| CF(혼잡 트래픽)| 샤딩·AI 등 추가 기술 없으면 혼잡 매우 클 수 있음     | PoS도 샤딩 없인 병목 심각  | 초대형 규모에서 둘 다 확장성 기술이 필요          |

#### **참고로 현재 기준 비트코인은 약 2만개, 이더리움은 1만개 이하의 노드가 활성화 되어있습니다.**

---

## **5. UBMS 독창적 기술 특징**

### **5.1. 완전 독립적 코드베이스**

UBMS는 기존 암호화폐 프로젝트와 차별화된 독창적 기술을 기반으로 합니다.  
타 프로젝트의 포크 없이 자체 개발된 코드베이스를 통해 기능 추가와 보안 강화를 실현합니다.

### **5.2. 합의 알고리즘**
가볍고 빠르게 작동하는 독자 개발한 합의알고리즘과    
PoW, PoS, PoB를 통합한 하이브리드 메커니즘을 도입하여 에너지 효율성과 네트워크 안정성을 극대화합니다.

### **5.3. 스마트 계약 대체 기술**

장차 업데이트할 동적 자가연산 블록(Dynamic Self-Computing Block) 기술을 통해 기존 스마트 계약의 한계를 극복하며 높은 유연성과 확장성을 제공할 예정입니다.

### **5.4. 역할다형성 자가조정 네트워크**

PSAN (Role-Polymorphic Self-Adjusting Network)는 네트워크 혼잡을 해결하기 위한 UBMS의 네트워크 독자 솔루션입니다.  
자세한 내용은 상기의 **4. 네트워크 구조**에 상세히 설명하였습니다.

### **5.5. UTXO 기반 메타데이터 스마트 컨트랙트**
UBMS (UTXO-Based Metadata Smart Contract)  
비트코인의 UTXO 모델을 기반으로 하면서도 스마트 컨트랙트를 실행할 수 있는 독창적 UBMS 구조를 미리 설계하였고,  
스마트 컨트랙트 부분은 UBMS의 동적 자가연산 블록(Dynamic Self-Computing Block) 기술로 장차 구현할 예정입니다.

#### **5.5.1. RGB 프로토콜 vs. 카르다노(eUTXO) vs. UBMS 비교**

| 비교 항목               | RGB 프로토콜                   | 카르다노(eUTXO)               | UBMS                          |
|-------------------------|--------------------------------|--------------------------------|------------------------------------------|
| 확장성                  | 제한적 확장                   | 병렬 처리로 높은 확장성        | 페이로드 기반으로 유연한 확장           |
| 표현 방식               | UTXO에 토큰 상태만 저장        | UTXO 자체에 검증 포함          | UTXO의 페이로드에서 수행                |
| 실행 방식               | 온체인 실행 불가능              | 트랜잭션 검증 시 실행 (온체인)  | 온체인/오프체인 혼합 방식               |
| 데이터 저장 위치        | 오프체인에서 관리               | 블록체인 내부에 저장           | UTXO 내부 페이로드로 저장               |
| 조건 기반 여부          | 지원하지 않음                   | 특정 조건 만족 시 실행        | CONDITION에서 조건 설정 후 실행         |
| 수명주기(TTL) 설정      | 지원하지 않음                   | 지원하지 않음                  | TTL 필드에 직접 포함                    |
| 변경 가능성             | 토큰 발행 후 변경 불가          | 한 번 생성된 eUTXO는 변경 불가 | 데이터 일부 수정 가능                   |
| 오프체인 데이터 저장    | 대부분 오프체인에서 처리        | 온체인에서 모든 검증 수행      | 일부 데이터를 오프체인에서도 관리       |
| 블록체인 과부하 문제     | 별도의 오프체인 검증 필요       | 온체인 실행으로 과부하 발생   | 페이로드 최적화로 과부하 방지            |
| 개발자 친화성           | 비트코인 스크립트 기반으로 복잡  | Plutus/Haskell 사용            | UTXO 기반으로 쉽게 사용                 |
| 보안성                  | 비트코인 보안 모델 유지         | 높은 보안                     | 블록체인+오프체인 조합으로 보안 강화      |

**UBMS는 사전에 확장성을 최우선에 두고 설계되었기에, 장차 기술 접목에 유리합니다.**

### **5.6. 독자기술 직렬화**

UBMS는 통신을 위한 경량 직렬화를 구현하였고 매우 유연하고 성능이 뛰어납니다.

#### **5.6.1. 직렬화 성능 및 특성 비교**

| **비교항목**   | **비트코인 직렬화**                                                | **이더리움 RLP**                                                                 | **UBMS 직렬화**                                                                |
|----------------|--------------------------------------------------------------------|----------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| **속도**       | 단순한 버퍼 조작으로 최소 오버헤드, 매우 빠름                        | 재귀적 처리와 길이 계산 등으로 오버헤드가 있어 느림                     | 템플릿 기반 최적화로 직접 메모리 복사하여 최고 빠름                              |
| **메모리**     | 간단한 버퍼 연산으로 메모리 사용이 매우 효율적                        | 동적 메모리 할당 및 재귀 호출로 추가 메모리 사용                             | 고정 사이즈 데이터 및 템플릿 처리로 불필요한 메모리 사용 최소화                   |
| **코드**       | 커스텀 구현이지만 구조가 단순하여 중간 정도의 복잡성                  | 다양한 데이터 타입과 중첩 구조라 복잡하고 구현 난이도가 높음                  | S_MESSAGE 공용체로 모든 유형의 구조체를 전달할 수 있어 간단함                     |
| **확장성**     | 고정된 데이터 구조로 확장이 제한적                                   | 다양한 데이터 구조 지원은 가능하나, 재귀적 설계로 확장 시 구현 복잡          | 템플릿 특수화로 새로운 데이터 타입 추가가 용이하여 확장이 뛰어남                   |
| **디버깅**     | 단순한 구조로 인해 디버깅 및 유지보수가 수월함                         | 복잡한 재귀 구조로 인해 에러 발생 시 추적 및 수정이 어려울 수 있음                   | 표준 C++ 코드와 템플릿 구조로 일관된 코드 사용으로 유지보수가 용이함              |
| **유연성**     | 특정 데이터 구조에 최적화되어 있어 유연성은 낮은 편                   | 다양한 데이터 타입과 중첩 지원하지만, 그에 따른 성능 저하가 단점             | 모든 유형의 데이터 전달 가능하며 성능이 뛰어남                                    |

#### **5.6.2. 평균 처리 시간**

| **직렬화 기법**         | **평균 처리 시간 (ms)** | **상세 설명**                                        |
|------------------------|-------------------------|------------------------------------------------------|
| **UBMS 직렬화**        | 0.15                    | 템플릿 기반 최적화와 직접 메모리 복사로 가장 빠름         |
| **FlatBuffers**        | 0.18                    | 빠른 메모리 접근 및 최소 오버헤드, 우수한 성능              |
| **Protocol Buffers**   | 0.20                    | 스키마 기반 직렬화로 효율적이나 약간의 오버헤드 존재         |
| **비트코인 직렬화**    | 0.25                    | 단순 버퍼 조작 방식으로 빠르나, UBMS보다는 다소 느림          |
| **Boost.Serialization**| 0.50                    | 복잡한 구조로 인한 오버헤드로 비교적 느림                 |
| **이더리움 RLP**       | 0.80                    | 재귀적 처리와 길이 계산 등으로 가장 많은 오버헤드 발생         |

### **5.7. 완전 분산형 구조**

#### **5.7.1. 비콘체인(Beacon Chain)이 없다**   
   - 비콘체인에 의존하지 않고 모든 노드가 독립적으로 합의 및 상태 갱신에 참여합니다.
   - 비콘체인이 없으므로 중앙 집중식 공격에 대한 위험이 줄어들고, 분산된 노드들이 직접 gossip과 DHT를 통해 상태를 검증하므로 보안성이 높아집니다.   
   - 중앙 집중식 장애점이 없으므로, 특정 체인에 문제가 생겨도 전체 네트워크가 영향을 받지 않습니다.   
   - 불필요한 체인 간 인터랙션을 제거하여 보안성과 안정성이 향상됩니다.
   - 중앙 관리 체계가 없기 때문에, 네트워크 규모가 커져도 릴레이와 투표자 수를 청사진에 따라 점진적으로 증가시켜 확장할 수 있습니다.
   - 향후 AI나 샤딩 기술과 결합하면, 더욱 고도화된 확장 솔루션으로 발전시킬 수 있습니다.

---



## **6. 가운영(준운영) 정의**

> 1. 오픈 베타 테스트 이후 실제 블록 생성 단계부터 ‘가운영’을 시작하며,  
>     월 단위로 지속적인 패치를 통해 코드 안정화 작업을 진행한다.  
> 2. 가운영 기간은 2026~2027년 소스코드를 GitHub에 공개하기 전까지 계속된다.  
> 3. 참여자는 미성숙한 코드로 인해 발생할 수 있는 각종 문제를 사전에 충분히 인지하였으므로,  
>     모든 참여자는 가운영 기간 중 발생하는 사건·사고를 감수한다.  
>     > **참여자**란 채굴자, 앱 사용자, UBMS 코인 프로젝트 생태계 참여자 일체를 말한다.  
> 4. 비트코인 개발 초기(약 2~3년) 동안 집중적으로 사건·사고가 발생한 사례를 참고하여,  
>     초기 운영 단계에서는 단계별 구분과 주의가 필요함을 모두가 인식하고 동의한다.  
> 5. 가운영 사실과 이에 동의하는 절차는 앱 시작 시 체크박스 형태로 표시하여,  
>     참여자로부터 명시적인 동의를 받는다.  
> 6. 가운영 기간 동안 예상되는 사건·사고 유형으로는  
>     시스템 공격(네트워크 DDoS, 노드 탈취 등), 블록 변조 시도, 코드 취약점을 노린 공격,  
>     체인 롤백, 그 외 버그로 인한 장애 등이 있다.  
> 7. 참여자는 가운영 기간 중 발생하는 모든 사건·사고가 코드 개발과 IT 서비스 운영의 필연적인 과정임을 인정하고,  
>     귀책을 묻지 아니하며, 개발 주체가 지속적인 시간과 노력을 투입해 문제를 해결하도록 조력한다.  
> 8. 가운영 상태에서는 홍보가 미미하여 참여자가 느리게 성장하기에,  
>     개발주체는 보유량 일부를 사용해 특정 참여자에게 자원의 집중이 되지 않도록 하거나,  
>     급과열·급냉각에 의한 시장가치 왜곡을 예방하고  
>     안정적인 성장을 조력한다.

---

## 7. 블록체인 위기 대응 매뉴얼

> ### **위기 대응 프로세스 및 책임 명시**
>
> 1. **위기상황 정의**  
>    - 해킹, 장애, 네트워크 공격, 블록체인 데이터 변조, 중대한 버그, 체인 롤백, 하드포크 및 기타 운영상 중대한 장애를 위기 상황으로 정의합니다.
>
> 2. **초기 대응 절차**  
>    - 문제가 발견될 경우 즉시 **개발자 또는 운영진이 긴급 점검 및 일시적 블록 생성을 중지**할 수 있습니다.
>    - 주요 이슈는 공식 커뮤니티 및 공지 채널(홈페이지, 포럼 등)에 신속하게 상황을 알립니다.
>
> 3. **조치 및 의사결정**  
>    - 장애 복구, 롤백, 하드포크 등 중대한 조치가 필요할 경우,  
>      **가운영 기간 중에는 개발자/운영진의 단독 판단으로 즉각적 패치 또는 롤백, 하드포크를 시행**할 수 있습니다.
>    - 조치 이후 상세 내역과 복구 절차, 영향 범위를 공식 채널을 통해 투명하게 안내합니다.
>
> 4. **인센티브 및 책임 범위**  
>    - 가운영 기간 중 발생한 모든 손실(코인 손실, 거래 오류 등)에 대해  
>      **참여자는 사전에 리스크를 충분히 인지하고 동의하며, 개발자 및 운영진에게 민·형사상 책임을 묻지 않습니다.**
>
> 5. **최종 결정권**  
>    - **정식 오픈(소스 공개) 이전까지 모든 긴급 상황의 최종 결정권은 개발자(또는 운영진)에 귀속**됩니다.
>    - **소스 공개전에는 개발자 또는 운영진이 임의의 판단 하에 즉각적으로 시스템 중단 및 복구 조치 가능합니다.**
>    - 오픈소스 전환 및 분산화 이후에는 커뮤니티 및 네트워크 합의에 따라 주요 결정을 진행합니다.


---

## 8. 참여자 위험 고지 (면책조항)

> ### **위험 고지 및 책임의 한계**
>
> 1. 본 프로젝트(UBMS)는 기술적 실험적 프로젝트로 금융투자 상품이나 증권이 아닙니다.
> 2. 회원정보 및 개인식별 정보를 수집하거나 관리하지 않습니다.
> 3. 오픈 베타 및 가운영(준운영) 상태로서,아직 코드 및 시스템의 완전성이 검증되지 않은 단계임을 명시합니다.
> 4. 모든 참여자(채굴자, 사용자, 노드 운영자 등)는  
>    다음의 위험을 사전에 충분히 인지하고, 이에 동의한 경우에만 참여해야 합니다:
>    - 해킹, 장애, 데이터 손실, 코인 소실, 체인 롤백, 하드포크, 임의의 코드 수정 등  
>      예기치 못한 문제로 인해 발생할 수 있는 **모든 손실**
> 5. 개발자 및 운영진은 가운영 기간 중 발생하는 모든 사건·사고에 대해  
>    **최대한 신속하고 성실하게 복구·대응**할 것이나,  
>    이로 인해 발생하는 **직·간접적 손실 및 책임에 대해 법적·금전적 책임을 지지 않습니다.**
> 6. 참여자는 앱, 지갑, 채굴 프로그램 실행 전 반드시  
>    **위험 고지 및 책임의 한계에 동의합니다**라는 체크박스 또는 동의 버튼을 확인해야 하며,  
>    이를 통한 동의 절차가 완료되지 않으면 시스템 이용이 제한됩니다.
> 7. 가운영 종료 및 소스 공개 이후에는,  
>    네트워크의 의사결정 및 운영 책임이 커뮤니티 및 네트워크 합의에 이관됩니다.

---


## 9. 로드맵

1. **오픈 베타 테스트 진행**  
   - 초기 기능을 검증하고, 사용자 피드백을 반영해 안정성을 높입니다.

2. **백서 버전 1.0 완성**  
   - 프로젝트 목표, 경제 모델, 기술 사양 등을 정리한 공식 문서를 완성합니다.

3. **가운영(준운영) 시작**  
   - PoW와 PoB 방식으로 실제 블록을 생성하며, 월 단위 패치를 통해 코드 안정화를 진행합니다.

4. **PoW 채굴 노드 50~100대 확보 시 참여용 코인 배포**  
   - 일정량의 PoW 채굴 노드가 확보되면, PoS 참여를 독려하기 위해 참여용 코인을 배포합니다.

5. **노드 증가에 따른 자원 분산화**  
   - 참여 노드가 늘어날수록 코인 자원이 분산되어 시장가치 왜곡이 줄어듭니다.

6. **2026~2027년 개발 소스 순차적 GitHub 공개**  
   - 단계별로 소스 코드를 오픈하여 누구나 검토·분석 및 코드 개발에 참여할 수 있도록 합니다.

7. **소스 공개를 통한 참여자 확대 및 개발 주도권 분산**  
   - 기존 개발 주체는 풀 리퀘스트 처리, 각종 테스트, 코드 검토 및 승인 등의 업무를 추가하며, 깃허브를 통해 모든 개발자에게 코드 기여 기회를 부여합니다.

8. **가운영(준운영) 종료**  
   - 코드 안정화와 충분한 노드 분산화를 달성한 후, 공식 운영 단계로 전환합니다.

9. **완전한 분산 운영(Decentralization) 달성**  
   - 운영 주체 없이도 네트워크가 자율적으로 유지·발전할 수 있는 구조를 완성합니다.

10. **비트코인과 이더리움 등 선례를 참고해 지속 진화**  
    - 모범적인 탈중앙화 생태계를 목표로, 참여자 모두가 합심하여 꾸준히 개선·진화합니다.

---   


