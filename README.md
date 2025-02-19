# **백서** UBMS  
**작성일:** 2024-11-26  
**버전:** 0.931

---

## **목차**
1. 소개  
    - 진화적개발  
    - 독립적 코드베이스  
    - 시대적 배경  
    - 방향  
2. 기술 개요  
3. 경제 모델  
    - 보상 분배  
    - 채굴 종류  
        - POW 작업증명  
        - POS 지분증명  
        - POB 행위증명  
    - 수수료  
        - 경제팩터  
        - 혼잡팩터  
        - 외부상수  
        - **수수료 계산**  
4. 네트워크 구조  
5. UBMS 독창적 기술 특징  
6. 보안 및 규정 준수  
7. 로드맵  
8. 개발자 소개  

---

## **1. 소개**

### **1.1. 진화적 개발**

UBMS 프로젝트는 진화적 발전 모델을 기반으로 설계되었습니다. 이는 단계별 개발과 지속적인 개선 및 기능 추가를 목표로 하며, 끊임없이 발전하는 블록체인을 지향합니다.  
초기 버전은 블록체인의 기본적인 형태로 출시되겠지만, 꾸준한 업데이트를 통해 점진적으로 발전할 예정입니다.  
사용자는 초기에는 다소 제한적인 기능만 제공될 수 있으나, 이는 안정적이고 혁신적인 시스템으로 나아가기 위한 필수적인 과정입니다.  
UBMS는 "꾸준함이 강함을 만든다"는 철학을 바탕으로 지속적인 개선을 약속합니다.

### **1.2. 독립적 코드베이스**

UBMS는 자체 개발 블록체인으로 서드파티 라이브러리와 개인 창작 코드를 활용하여 개발되었습니다.  
이 프로젝트는 타 코인을 복사하거나 포크하지 않고, 독자적인 진화를 이루기 위한 토대를 마련함으로써 향후 발전 가능성을 극대화합니다.

### **1.3. 시대적 배경**

블록체인은 이미 학문 및 교육 커리큘럼에 포함된 혁신 기술로 자리 잡았으며, 금융 산업 및 다양한 산업 분야에서 중요한 역할을 수행하고 있습니다.  
세계 각국은 연구 및 개발에 막대한 자금을 투입하고 있으나, 기술 발전 속도는 여전히 도전 과제로 남아있습니다.

### **1.4. 방향**

UBMS(UTXO-Based Metadata Smart Contract)는 기존 비트코인의 한계를 극복하고자 독창적인 기술적 접근을 시도합니다.  
소규모 기업이지만 열정과 의지를 바탕으로, 시대의 필요에 부합하는 기술을 지속적으로 개발해 나갈 것입니다.

---

## **2. 기술 개요**

_(내용 작성 중)_

---

## **3. 경제 모델**

### **3.1. 보상 분배 규칙**

UBMS의 채굴 보상은 채굴자의 기여도에 따라 공정하게 분배됩니다.  
각 채굴자가 제출한 공유 블록(Share)의 수에 기반하여 보상이 산출되며, 이는 투명성을 극대화하기 위한 핵심 메커니즘입니다.

#### **보상 분배 공식**
채굴 보상은 다음과 같이 계산됩니다:

# $$B_i = R \times \frac{S_i}{S_{\text{total}}}$$

- $$B_i$$: 채굴자 $$i$$가 받을 보상  
- $$R$$: 블록 생성 시 총 보상  
- $$S_i$$: 채굴자 $$i$$가 제출한 유효 공유 블록 수  
- $$S_{\text{total}}$$: 모든 채굴자가 제출한 유효 공유 블록 수의 합

---

#### **예시**

총 보상 $$R = 100$$ UBMS 코인이고,  
채굴자 A, B, C의 기여도가 각각 50, 30, 20일 경우:

- **채굴자 A:**  
  ## $$B_A = 100 \times \frac{50}{100} = 50 \, \text{UBMS}$$
- **채굴자 B:**  
  ## $$B_B = 100 \times \frac{30}{100} = 30 \, \text{UBMS}$$
- **채굴자 C:**  
  ## $$B_C = 100 \times \frac{20}{100} = 20 \, \text{UBMS}$$

---

### **3.2. POW 작업증명 채굴**

#### **3.2.1. 초반 채굴 설정**

**기본 계산**  
- **채굴 기간:** 6시간 = $$6 \times 60 \times 60 = 21,600$$초  
- **블록 생성 시간:** 10초/block  
- **총 블록 수:** $$\frac{21,600}{10} = 2,160$$블록  

**반감기 간격 및 보상 설정**  
- **반감기 간격 $$H$$:** 720블록 (2시간)  
- **초기 보상 $$R_0$$:** 794개/block  
- **총 반감기 횟수 $$N$$:** 3회  

**초기 채굴 단계 요약**  
- **총 채굴 코인 수 $$C_1$$:**  
  # $$C_1 = (794 \times 720) + (397 \times 720) + (198.5 \times 720) \approx 1,000,440 \, \text{개}$$  

---

#### **3.2.2. 후반 채굴 설정**

**기본 계산**  
- **반감기 간격:** 2년  
- **블록 생성 시간:** 10분/block  
- **반감기 간격 블록 수 $$H'$$:**  
  ## $$H' = 2 \times 365 \times \frac{24 \times 60}{10} = 105,120 \, \text{블록}$$  

**후반 채굴 단계 요약**  
- **총 채굴 코인 수 $$C_2$$:**  
  # $$C_2 = \sum_{k=0}^{9} \left( \frac{R_0'}{2^k} \times H' \right) \approx 19,985,296 \, \text{개}$$  

---

#### **3.2.3. 비트코인과 비교**

**비트코인의 채굴 구조**  
1. **블록 생성 시간:** 10분/block  
2. **반감기 간격:** 210,000블록 (약 4년)  
3. **초기 보상:** 50 BTC/block  
4. **총 공급량:** 21,000,000 BTC  

**반감기 간격 및 보상 비교**

| **구분**           | **비트코인**                   | **UBMS**                         |
|--------------------|--------------------------------|----------------------------------|
| 반감기 간격        | 210,000블록 (약 4년)            | 105,120블록 (약 2년)              |
| 초기 보상          | 50 BTC/block                   | 95 UBMS/block                    |
| 총 공급량          | 21,000,000 BTC                 | 약 20,000,000 코인               |

---

#### **3.2.4. 채굴 설정 결론**

| **단계**      | **총 채굴 코인 수** | **총 블록 수**  | **반감기 간격**         | **초기 보상**   | **총 반감기 횟수** |
|---------------|--------------------|-----------------|-------------------------|-----------------|-------------------|
| 초반 채굴     | 1,000,440개        | 2,160블록       | 720블록 (2시간)         | 794개/block     | 3회               |
| 후반 채굴     | 19,985,296개       | 1,051,200블록   | 105,120블록 (2년)       | 95개/block      | 10회              |

---

#### **3.2.5. 높이 2160 근방 초기/후기 전환시 LOG**

| 블록 높이 | 이전 `총공급량`         | 현재 `총공급량`         | 증가량           | `보상`           | `반감기` |
|-----------|-------------------------|-------------------------|------------------|------------------|----------|
| 2155      | 99,821,655,554,920      | 99,841,444,443,808      | 19,788,888,888   | 19,788,888,888   | 2        |
| 2156      | 99,841,444,443,808      | 99,861,233,332,696      | 19,788,888,888   | 19,788,888,888   | 2        |
| 2157      | 99,861,233,332,696      | 99,881,022,221,584      | 19,788,888,888   | 19,788,888,888   | 2        |
| 2158      | 99,881,022,221,584      | 99,900,811,110,472      | 19,788,888,888   | 19,788,888,888   | 2        |
| 2159      | 99,900,811,110,472      | 99,920,599,999,360      | 19,788,888,888   | 19,788,888,888   | 2        |
| 2160      | 99,920,599,999,360      | 99,930,099,999,360      | 9,500,000,000    | 9,500,000,000    | 0        |
| 2161      | 99,930,099,999,360      | 99,939,599,999,360      | 9,500,000,000    | 9,500,000,000    | 0        |
| 2162      | 99,939,599,999,360      | 99,949,099,999,360      | 9,500,000,000    | 9,500,000,000    | 0        |

---

### **3.3. 수수료**

#### **3.3.1. 경제팩터**

_(내용 작성 중)_

---

#### **3.3.2. 혼잡팩터**

_(내용 작성 중)_

---

#### **3.3.3. 외부상수**

_(내용 작성 중)_

---

#### **3.3.4. 수수료 계산**

외부에서 수신한 1ubms의 시장가를 바탕으로, 네트워크 혼잡 인자를 동적으로 반영한 수수료 계산 공식을 제시한다.  
초기 액면가 기준으로 1ubms당 시장가를 **10,000원**으로 설정하며, 이 때의 수수료는 **1,000원**으로 정한다.  
시장이 고평가되어 1ubms당 시장가가 **100,000,000원**에 도달할 경우, 수수료는 **100,000원**으로 산출된다.

# **수수료 공식 전개**

최종 수수료 \( F \)는 아래와 같이 계산된다.

\[
F = 1000 \times \left(\frac{v}{10\,000}\right)^{0.5} \times CF \quad = \quad 1000 \times \sqrt{\frac{v}{10\,000}} \times CF
\]

여기서,  
- \( F \)는 최종 수수료 (원 단위)  
- \( v \)는 1ubms의 시장가 (원 단위)  
- \( CF \)는 네트워크 혼잡 인자 (기본값 1.0, 네트워크 혼잡 시 1.0보다 큰 값)

## 전개식 상세 설명

### 1. 기본 설정
- 기준 시장가: \( v_0 = 10\,000 \)원  
- 기준 수수료: \( F_0 = 1000 \)원  
- 네트워크 혼잡 인자: \( CF \) (혼잡 시 가중치를 적용)

### 2. 시장가에 따른 수수료 조정

현재 시장가 \( v \)에 따라, 수수료는 다음 비율로 조정된다.

\[
\left(\frac{v}{10\,000}\right)^{0.5} \quad = \quad \sqrt{\frac{v}{10\,000}}
\]

### 3. 최종 수수료 산출

최종 수수료 \( F \)는 기준 수수료에 경제 인자와 네트워크 혼잡 인자를 곱하여 결정된다.

\[
F = 1000 \times \sqrt{\frac{v}{10\,000}} \times CF
\]

#### 예시 1: 
- \( v = 10\,000 \)원, \( CF = 1.0 \)

\[
F = 1000 \times \sqrt{\frac{10\,000}{10\,000}} \times 1.0 = 1000 \times 1 \times 1.0 = 1000 \text{원}
\]

#### 예시 2:
- \( v = 100\,000\,000 \)원, \( CF = 1.0 \)

\[
F = 1000 \times \sqrt{\frac{100\,000\,000}{10\,000}} \times 1.0 = 1000 \times \sqrt{10\,000} \times 1.0 = 1000 \times 100 = 100\,000 \text{원}
\]

## 결론

제시한 수수료 공식은 외부에서 수신한 시장가와 네트워크 혼잡 인자를 동적으로 반영하여,  
- 시장가가 낮은 경우(1ubms당 10,000원 기준)에는 1,000원의 수수료가,  
- 시장가가 높은 경우(1ubms당 100,000,000원 기준)에는 100,000원의 수수료가 산출되도록 설계되었다.

---

## **4. 네트워크 구조**  
_(내용 작성 중)_

---

## **5. UBMS 독창적 기술 특징**

UBMS는 기존 암호화폐 프로젝트와 차별화된 독창적 기술을 기반으로 한다.  
- **완전 독립적 코드베이스:**  
  타 프로젝트의 포크 없이 자체 개발된 코드베이스를 통해 혁신적 기능 추가와 보안 강화를 실현한다.  
- **혁신적 합의 알고리즘:**  
  PoW, PoS, PoB를 통합한 하이브리드 메커니즘을 도입하여 에너지 효율성과 네트워크 안정성을 극대화한다.  
- **스마트 계약 대체 기술:**  
  동적 자가연산 블록(Dynamic Self-Computing Block) 기술을 통해 기존 스마트 계약의 한계를 극복하며 높은 유연성과 확장성을 제공한다.  
- **UTXO 기반 메타데이터 스마트 컨트랙트(UBMS):**  
  비트코인의 UTXO 모델을 기반으로 하면서도 스마트 컨트랙트를 실행할 수 있는 독창적 구조를 구현한다.

---

## **6. 보안 및 규정 준수**  
_(내용 작성 중)_

---

## **7. 로드맵**  
_(내용 작성 중)_

---

## **8. 개발자 소개**  
bokkamsun@gmail.com

---
