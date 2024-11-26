## **백서** UBMS
**작성일:** 2024-11-26  
**버전:** 0.907  

---

## **목차**
1. 소개
    - 진화적개발
    - 독립적 코드베이스
    - 시대적 배경
    - 방향
3. 기술 개요
4. 경제 모델  
    - 보상 분배
    - 채굴 종류
        - POW 작업증명
        - POS 지분증명
        - POB 행위증명
5. 네트워크 구조
6. UBMS 독창적 기술 특징
7. 보안 및 규정 준수
8. 로드맵
9. 개발자 소개  

---

## **1. 소개**
### **1.1. 진화적 개발**

UBMS 프로젝트는 진화적 발전 모델을 기반으로 설계되었습니다. 이는 단계별 개발과 지속적인 개선 및 기능 추가를 목표로 하며, 끊임없이 발전하는 블록체인을 지향합니다.  
초기 버전은 블록체인의 기본적인 형태로 출시되겠지만, 꾸준한 업데이트를 통해 점진적으로 발전할 예정입니다.  
사용자는 초기에는 다소 제한적인 기능만 제공될 수 있지만, 이는 안정적이고 혁신적인 시스템으로 나아가기 위한 필수적인 과정입니다. UBMS는 "꾸준함이 강함을 만든다"는 철학을 바탕으로 지속적인 개선을 약속합니다.

### **1.2. 독립적 코드베이스**

UBMS는 자체개발 블록체인으로 서드파티 라이브러리와 개인 창작코드로 개발되었습니다. 이는 학습 목적으로 시작된 프로젝트의 특징이기도 하지만, 
여타 코인을 복사하거나 포크하지 않았기에 미래 발전가능성을 종속당하지 않고 독자적인 진화를 이룰 토대를 갖게 되었습니다. 이것이야 말로 가장 큰 장점입니다.

독립적 코드베이스 기반의 프로젝트는 초기에는 다소 어려움이 있을 수 있지만, 점진적인 개선과 외부 컨트리뷰터의 참여로 발전과 안정화를 이룰 것입니다.
본 프로젝트는 블록체인 기술의 본질적 가치를 반영하며, 창의적이고 독창적인 방식으로 새로운 가능성을 탐구합니다. UBMS는 느리지만 꾸준히 성장하며, 사용자와 개발자 모두에게 신뢰를 제공할 것을 약속합니다.

### **1.3. 시대적 배경**

블록체인은 이미 학문으로 자리 잡아 교육 커리큘럼에 포함된 지 오래이며, 산학연의 혁신 아이콘이자 금융 산업의 중요한 축으로 자리 잡았습니다.  
세계 각국은 매년 천문학적인 자금을 연구 단체와 기업에 투입하며 이 산업의 주도권을 확보하기 위해 노력하고 있습니다. 그러나 이러한 노력과 투자 규모에 비해 기술 발전 속도는 기대보다 더디게 진행되고 있습니다.  

초기 블록체인의 핵심 아이디어는 변조 불가능한 해시 기술, 채굴, 합의 알고리즘으로 요약되며, 최근에 등장하는 기술은 주로 통신 속도 개선에 초점이 맞춰졌습니다. 블록체인의 근본적인 구조적 특성 때문에 체결 및 통신 속도가 발목을 잡히고 있기 때문입니다.  
군계일학으로 이더리움의 EVM 기술은 원장을 유지하기 위해 필요한 막대한 컴퓨팅 자원을 가상 컴퓨팅으로 활용한다는 점에서 기존의 아이디어 중 가장 혁신적인 접근 방식이라 평가합니다.  

블록체인의 등장은 엄청난 시장 파급 효과를 보여주었지만 ,동시대에 등장한 AI 산업과 비교해 보면, 블록체인의 기술 응용 범위는 상당히 제한적입니다.
관련 법률과 세법이 정교해지고, 거래가 관공서나 중앙 기관에 의해 통제되는 시대가 온다면, 블록체인은 기존 데이터베이스 기술과의 비교우위마저 약화될 가능성이 있습니다.  

그러나 이러한 한계에도 불구하고 블록체인은 여전히 화폐, 투자 상품, 금융 시스템의 중요한 역할을 지속적으로 수행할 것입니다.  
본인은 과거부터 구상해 온 여러가지 좋은 아이디어가 있습니다. 조금씩 풀어내겠습니다. 
사용자 여러분께서도 분명 좋아 하실것입니다.

### **1.4. 방향**

제가 아니라도 많은 코인들이 존재합니다. 이들의 행보를 따라 갈 생각이라면 이 프로젝트는 탄생하지 않았을 것입니다.
상술한 시대적 배경에 따라, 시대가 필요한 기술이 되고자 항상 창조적이고 무모한 도전을 과감하게 시도할 것입니다. 
백서의 버전이 올라가면 구체적인 계획과 설명을 업데이트 할 것입니다.

---

## **2. 기술 개요**

---

## **3. 경제 모델**
### **3.1. 보상 분배 규칙**

UBMS의 채굴 보상은 공정한 분산화를 보장하기 위해 채굴자의 기여도에 따라 나눠집니다. 이를 위해 마이닝 풀 방식을 적용하여 각 채굴자가 제출한 공유 블록(Share)의 수를 기준으로 보상을 계산합니다.

#### **보상 분배 공식**
채굴 보상은 다음과 같이 계산됩니다:

# $$B_i = R \times \frac{S_i}{S_{\text{total}}}$$

- $$B_i$$: 채굴자 $$i$$가 받을 보상
- $$R$$: 블록 생성 시 총 보상
- $$S_i$$: 채굴자 $$i$$가 제출한 유효 공유 블록 수
- $$S_{\text{total}}$$: 모든 채굴자가 제출한 유효 공유 블록 수의 합

#### **분배 과정**
1. **기여도 기록**: 각 채굴자가 블록 채굴 작업에 기여한 유효 공유 블록의 수를 기록합니다.
2. **보상 계산**: 기여 비율 $$\frac{S_i}{S_{\text{total}}}$$을 바탕으로 각 채굴자에게 보상을 분배합니다.
3. **결과 저장**: 분배 결과는 블록체인에 저장되어 투명성을 보장합니다.

---

#### **예시**
총 보상 $$R = 100$$ UBMS 코인이고, 채굴자 A, B, C가 다음과 같은 기여도를 가졌다고 가정합니다:
- 채굴자 A: $$S_A = 50$$
- 채굴자 B: $$S_B = 30$$
- 채굴자 C: $$S_C = 20$$
- $$S_{\text{total}} = S_A + S_B + S_C = 100$$

**보상 계산:**
- 채굴자 A:  
  $$B_A = 100 \times \frac{50}{100} = 50 \, \text{UBMS}$$
- 채굴자 B:  
  $$B_B = 100 \times \frac{30}{100} = 30 \, \text{UBMS}$$
- 채굴자 C:  
  $$B_C = 100 \times \frac{20}{100} = 20 \, \text{UBMS}$$

이 방식은 네트워크의 모든 채굴자가 기여한 만큼의 공정한 보상을 받을 수 있도록 설계되었습니다.

---

### **3.2. POW 작업증명 채굴**

#### **3.2.1. 초반 채굴 설정**

**기본 계산**  
- **채굴 기간:** 6시간 = $$6 \times 60 \times 60 = 21,600$$초  
- **블록 생성 시간:** 1초/block  
- **총 블록 수:** 21,600블록  

**반감기 간격 및 보상 설정**  
초반 채굴에서는 6시간 내에 1,000,000개의 코인을 채굴하기 위해 아래와 같은 설정을 적용합니다:

- **반감기 간격 $$H$$:** 7,200블록 (2시간)  
- **초기 보상 $$R₀$$:** 80개/block  
- **총 반감기 횟수 $$N$$:** 3회  
- **목표 총 채굴량:** 1,000,000개  

**보상 스케줄 및 총 채굴량**  

| **반감기 횟수 $$k$$** | **블록 보상 $$R₀ / 2^k$$** | **블록 수 $$H$$** | **채굴된 코인 수 $$R₀ / 2^k \times H$$** |
|-----------------------|-----------------------------|-------------------|-------------------------------------|
| 0                     | 80개/block                 | 7,200             | 576,000                             |
| 1                     | 40개/block                 | 7,200             | 288,000                             |
| 2                     | 20개/block                 | 7,200             | 144,000                             |

**초기 채굴 단계 요약**  
- **총 채굴 코인 수 $$C₁$$:**  
  
  # $$C₁ = \sum_{k=0}^{N₁-1} \left( \frac{R₀}{2^k} \times H \right) + \left( \frac{R₀}{2^{N₁}} \times (T₁ - N₁ \times H) \right)$$

- 계산 결과:  

  ## $$C₁ = (80 \times 7,200) + (40 \times 7,200) + (20 \times 7,200) + (19 \times 7,200) \approx 1,008,000 \, \text{개}$$

---

#### **3.2.2. 후반 채굴 설정**

**기본 계산**  
- **채굴 기간:** 20년  
- **블록 생성 시간:** 1분/block  
- **총 블록 수:** $$20 \times 365 \times 24 \times 60 = 10,512,000$$블록  
- **목표 총 채굴량:** 20,000,000개  

**반감기 간격 및 보상 설정**  
후반 채굴에서는 20년 동안 20,000,000개의 코인을 채굴하기 위해 아래와 같은 설정을 적용합니다:

- **반감기 간격 $$H'$$:** 200,000블록 (~138.89일)  
- **초기 보상 $$R₀'$$:** 50개/block  

**보상 스케줄 및 총 채굴량**  

| **반감기 횟수 $$k$$** | **블록 보상 $$R₀' / 2^k$$** | **블록 수 $$H'$$** | **채굴된 코인 수 $$R₀' / 2^k \times H'$$** |
|-----------------------|-----------------------------|--------------------|---------------------------------------|
| 0                     | 50개/block                 | 200,000            | 10,000,000                             |
| 1                     | 25개/block                 | 200,000            | 5,000,000                              |
| 2                     | 12.5개/block               | 200,000            | 2,500,000                              |
| 3                     | 6.25개/block               | 200,000            | 1,250,000                              |

**후반 채굴 단계 요약**  
- **총 채굴 코인 수 $$C₂$$:**  

  # $$C₂ = \sum_{k=0}^{\infty} \left( \frac{R₀'}{2^k} \times H' \right) = R₀' \times H' \times 2 = 20,000,000 \, \text{개}$$

---

### **3.2.3. 채굴 설정 결론**

| **단계**       | **총 채굴 코인 수** | **총 블록 수** | **반감기 간격**         | **초기 보상** | **총 반감기 횟수** |
|----------------|--------------------|----------------|-------------------------|---------------|-------------------|
| **초기 채굴**  | 1,008,000개       | 21,600블록     | 7,200블록 (2시간)       | 80개/block    | 3회               |
| **후반 채굴**  | 20,000,000개      | 10,512,000블록 | 200,000블록 (~138.89일) | 50개/block    | 53회              |

---

## **4. 네트워크 구조**  
_(내용 작성 중)_  

---

## **5. UBMS 독창적 기술 특징**

UBMS는 기존 암호화폐 프로젝트와 기술적 차별점을 강조하며, 다음과 같은 독창적인 특징을 갖추고 있습니다:

- **완전 독립적 코드베이스**:  
  UBMS는 기존 프로젝트의 포크(fork) 기반이 아닌, 완전히 새롭게 자체 설계된 독립적인 코드베이스를 사용합니다. 이는 확장에 매우 유리한 포지션으로 상상하는 바 모두 구현할수 있는 창작의 기초토대를 확실히 가져가고 있습니다. 혁신적 기능 추가, 보안 강화등등의 모든 독창적 설계를 가능하게 하는 기반입니다.

- **혁신적 합의 알고리즘**:  
  기존의 PoW(작업증명), PoS(지분증명) 및 PoB(행위증명) 모델을 순차적으로 업데이트할 예정이며, 이를 각각 개별로 작동하게 하거나, 통합하여 하이브리드 합의 메커니즘을 채택할 계획으로 에너지 효율성과 네트워크 안정성을 모두 충족하기 위해노력합니다.

- **스마트 계약 대체 기술**:  
  UBMS는 기존 스마트 계약보다 강력한 **동적 자가연산 블록(Dynamic Self-Computing Block)** 기술을 추가할 예정이며 더 높은 유연성과 확장성을 제공하려 노력합니다.

- **모듈화된 아키텍처**:  
  네트워크의 각 구성 요소는 완전히 모듈화되어 있으며, 새로운 기능 추가 및 유지보수가 용이합니다.

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
