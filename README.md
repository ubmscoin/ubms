# **백서** UBMS  
**작성일:** 2024-11-26  
**버전:** 0.953

---

## **목차**
1. 소개  
   1.1. 진화적 개발  
   1.2. 독립적 코드베이스  
   1.3. 시대적 배경  
   1.4. 방향  
2. 기술 개요  
3. 경제 모델  
   3.1. 보상 분배  
   3.2. 채굴 종류  
       3.2.1. POW 작업증명 채굴  
           3.2.1.1. 초반 채굴 설정  
           3.2.1.2. 후반 채굴 설정  
           3.2.1.3. 비트코인과 비교  
           3.2.1.4. 채굴 설정 결론  
           3.2.1.5. 높이 2160 근방 초기/후기 전환시 LOG  
       3.2.2. POS 지분증명 채굴  
   3.3. 수수료  
       3.3.1. 경제팩터  
       3.3.2. 혼잡팩터  
       3.3.3. 외부변수,내부상수  
       3.3.4. 수수료   
       3.3.5. 비트코인과 이더리움의 수수료 비교  
4. 네트워크 구조  
5. UBMS 독창적 기술 특징  
6. 보안 및 규정 준수  
7. 로드맵  
8. 개발자 소개  

---

## **1. 소개**

### **1.1. 진화적 개발**

UBMS 프로젝트는 진화적 발전 모델을 기반으로 설계됩니다.  
단계별 개발과 지속적인 개선 및 기능 추가를 목표로 하며, 끊임없이 발전하는 블록체인을 지향합니다.  
초기 버전은 블록체인의 기본적인 형태로 출시되나, 지속적인 업데이트를 통해 점진적으로 발전할 예정입니다.  
사용자에게는 초기에 다소 제한적인 기능만 제공되나, 이는 안정적이고 혁신적인 시스템으로 나아가기 위한 필수적인 과정입니다.  
UBMS는 블록체인을 장기프로젝트로 삼아 "꾸준함이 승자의 유일한 전술이다"라는 철학에 따라 지속적인 개선을 약속합니다.

### **1.2. 독립적 코드베이스**

UBMS는 자체 개발 블록체인으로, 서드파티 라이브러리와 개인 창작 코드를 활용하여 개발됩니다.  
타 코인을 복사하거나 포크하지 않고 스스로 생산한 코드로 전체 프로젝트를 완전히 통제하며, 
기존 레거시코드와 커플링이 없기에 모든 코드조각을 자유롭게 가공할수 있고,  외부기술 종속에서 자유롭습니다.
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

_(내용 작성 중)_

---

## **3. 경제 모델**

### **3.1. 보상 분배 규칙**

UBMS의 채굴 보상은 채굴자의 기여도와 참여자의 지분에 따라 공정하게 분배됩니다.

---

### **3.2. 채굴 종류**

#### **3.2.1. POW 작업증명 채굴**

##### **3.2.1.1 초반 채굴 설정**

**작업증명 채굴은 지분증명 채굴과 일정비율로 나누게 됩니다. 아래는 나누기전 채굴 총량을 기준으로 계산합니다.**  

**기본 계산**  
- **채굴 기간:** 6시간 = $$6 \times 60 \times 60 = 21,600 \, \text{초}$$  
- **블록 생성 시간:** 10초/block  
- **총 블록 수:** $$\frac{21,600}{10} = 2,160 \, \text{블록}$$  

**반감기 간격 및 보상 설정**  
- **반감기 간격 $$H$$:** 720블록 (2시간)  
- **초기 보상 $$R_0$$:** 794개/block  
- **총 반감기 횟수 $$N$$:** 3회  

**초기 채굴 단계 요약**  
- **총 채굴 코인 수 $$C_1$$:**  
  ## $$C_1 = (794 \times 720) + (397 \times 720) + (198.5 \times 720) \approx 1,000,440 \, \text{개}$$

##### **3.2.1.2 후반 채굴 설정**

**기본 계산**  
- **반감기 간격:** 2년  
- **블록 생성 시간:** 10분/block  
- **반감기 간격 블록 수 $$H'$$:**  
  ## $$H' = 2 \times 365 \times \frac{24 \times 60}{10} = 105,120 \, \text{블록}$$

**후반 채굴 단계 요약**  
- **총 채굴 코인 수 $$C_2$$:**  
  # $$C_2 = \sum_{k=0}^{9} \left( \frac{R_0'}{2^k} \times H' \right) \approx 19,985,296 \, \text{개}$$

##### **3.2.1.3 비트코인과 비교**

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

##### **3.2.1.4 채굴 설정 결론**

| **단계**      | **총 채굴 코인 수** | **총 블록 수**  | **반감기 간격**         | **초기 보상**   | **총 반감기 횟수** |
|---------------|--------------------|-----------------|-------------------------|-----------------|-------------------|
| 초반 채굴     | 1,000,440개        | 2,160블록       | 720블록 (2시간)         | 794개/block     | 3회               |
| 후반 채굴     | 19,985,296개       | 1,051,200블록   | 105,120블록 (2년)       | 95개/block      | 10회              |

##### **3.2.1.5 높이 2160 근방 초기/후기 전환시 LOG**

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

#### **3.2.2. POS 지분증명 채굴**

POS 채굴 보상은 전체 채굴 보상액을 채굴자와 스테이킹 참여자 간에 공정하게 분배하는 방식으로 이루어집니다.  
여기서는 예시로 총 보상이 **100 코인**인 경우를 가정합니다.

- **채굴자 보상:**  
  순수 채굴자는 전체 보상의 20%를 배분받습니다. (**작업증명**)  
  따라서, 100 코인 중 20%에 해당하는 20 코인이 채굴자에게 지급됩니다.

- **스테이킹 참여자 보상:**  
  나머지 80%인 80 코인은 스테이킹 참여자들이 자신이 보유한 지분 비율에 따라 분배받습니다. (**지분증명**)  
  예를 들어, 3명의 스테이킹 참여자가 각각 10 코인, 30 코인, 60 코인의 지분을 보유하고 있다고 가정하면,  
  전체 스테이킹 지분은 10 + 30 + 60 = 100 코인이 되고,  
  각 스테이킹 참여자가 받는 보상은 다음과 같이 계산됩니다.

  - **스테이커 1:**  
    ## $$80 \times \frac{10}{100} = 8 \, \text{코인}$$
    
  - **스테이커 2:**  
    ## $$80 \times \frac{30}{100} = 24 \, \text{코인}$$
    
  - **스테이커 3:**  
    ## $$80 \times \frac{60}{100} = 48 \, \text{코인}$$

따라서,  
- 총 보상 100 코인 중 순수 채굴자는 **20 코인** 을,  
- 스테이킹 참여자들은 각각 **8 코인**, **24 코인**, **48 코인**을 받게 됩니다.

이와 같이 UBMS의 POS 보상 분배 방식은 전체 보상의 20%를 채굴자에게,  
나머지 80%를 스테이킹 참여자들이 자신이 보유한 지분 비율에 따라 공정하게 분배받도록 설계되어 있습니다.

---

#### **3.2.3. POB 행위증명 채굴**  
_(내용 작성 중)_

---

### **3.3. 수수료**

#### **3.3.1. 경제팩터**

경제팩터는 외부에서 수신한 1 UBMS의 시장가를 기준으로 기저 수수료를 산출하기 위한 보정값입니다.  
외부 데이터(예: 코인마켓캡, 가격공시 사이트)에서 제공되는 시장가를 기준으로,  
기준 시장가 $$v_0 = 10\,000 \, \text{원}$$에 대해 기저 수수료 $$B$$가 결정됩니다.  
이를 바탕으로 경제팩터 $$EF$$는 다음과 같이 정의됩니다:

# $$EF = \left(\frac{v}{v_0}\right)^{0.5} \quad = \quad \sqrt{\frac{v}{10\,000}}$$

시장가가 상승할수록 경제팩터는 증가하여 기저 수수료를 보정합니다.  
기존 비트코인 및 이더리움은 고정 수수료 또는 부적절한 동적 수수료 정책으로 높은 수수료를 유발하는 반면,  
UBMS는 외부 시장 데이터를 기반으로 한 경제팩터 도입으로 합리적인 수수료를 유지합니다.

---

#### **3.3.2. 혼잡팩터**

혼잡팩터는 최근 250개 블록의 네트워크 혼잡도를 측정하여 산출됩니다.  
네트워크에 대기 중인 거래 수를 기반으로 하며, 혼잡도가 높을 경우 혼잡팩터 $$CF$$는 1.0보다 큰 값으로 조정됩니다.  
이를 통해 네트워크 혼잡 상황에서는 추가 수수료를 인상하여 스팸 트랜잭션을 방지하고,  
네트워크의 안정성을 확보할 수 있도록 설계되어 있습니다.

---

#### **3.3.3. 외부변수**

항상 부정확한 경제팩터를 얻기위해 트랜잭션을 조사하여 시장가를 추론할 필요없습니다 .
우리가 알고싶어하는 시장가는 시스템 밖의 코인마켓캡과 같은 가격공시 사이트로부터 수신되는 외부정보를 참고합니다.  
이 변수값은 1 UBMS당 시장가의 기준 가격을 제공하며, 기저 수수료 산출에 필수적입니다.  
기존 업체들은 내부 계산 방식에만 의존하다보니 비현실적인 높은 수수료 정책을 적용하는 경우가 많으나,  
UBMS는 외부 데이터를 활용하여 보다 현실적이고 합리적인 수수료 정책을 구현합니다.
* 개발 시점인 지금은 유통될수 없어 외부에서 시장가를 얻을수 없기에, 내부상수 액면가만 적용합니다.
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

   도표는 비트코인과 이더리움 혼잡팩터 CF  1.0을 기준으로 네트워크 혼잡시 10배까지 증액됩니다.
   송금 1,000원에 수수료 5,000원? 혼잡시 10배 10,000 ~ 50,000 원?  
   급격한 혼잡이나 특정 이벤트(예: 대규모 ICO, NFT 발매 등)가 발생하면,심지어 1건당 수수료가 30,000원에서 50,000원 이상으로 급등하는 사례도 보고되고 있습니다.
   비트코인과 이더리움의 수수료가 불합리한것은 네트워크 내부 트랜잭션을 모집단으로 EF를 산출하기 때문입니다.
   자유시장 경제에 의존하여 수요공급으로 가치가 결정되는 암호화폐가 화폐유통을 중계하거나 시장가치를 공시하는 거래소의 등장을 예측하지 못했을까요?
   개발자의 아집과 외부시장과 시스템과의 소통단절이 부른 대참사라고 할수있습니다.

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
_(내용 작성 중)_

---

## **5. UBMS 독창적 기술 특징**

UBMS는 기존 암호화폐 프로젝트와 차별화된 독창적 기술을 기반으로 합니다.  
- **완전 독립적 코드베이스:**  
  타 프로젝트의 포크 없이 자체 개발된 코드베이스를 통해 혁신적 기능 추가와 보안 강화를 실현합니다.
- **혁신적 합의 알고리즘:**  
  PoW, PoS, PoB를 통합한 하이브리드 메커니즘을 도입하여 에너지 효율성과 네트워크 안정성을 극대화합니다.
- **스마트 계약 대체 기술:**  
  장차 업데이트할 동적 자가연산 블록(Dynamic Self-Computing Block) 기술을 통해 기존 스마트 계약의 한계를 극복하며 높은 유연성과 확장성을 제공할 예정입니다.
- **UTXO 기반 메타데이터 스마트 컨트랙트**  
  (UBMS: UTXO-Based Metadata Smart Contract)  
  비트코인의 UTXO 모델을 기반으로 하면서도 스마트 컨트랙트를 실행할 수 있는 독창적 구조를 구현합니다.
  
  **RGB 프로토콜 vs. 카르다노(eUTXO) vs. UBMS** 비교  
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

---

## **6. 보안 및 규정 준수**  
_(내용 작성 중)_

---

## **7. 로드맵**  
_(내용 작성 중)_

---

## **8. 개발자 소개**  
bokkamsun@gmail.com
