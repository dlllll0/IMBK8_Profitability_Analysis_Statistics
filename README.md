# IMBK8_Profitability_Analysis_Statistics  
  
#### 🏦 iM뱅크 중소기업 수익 세분화 및 알짜 고객 발굴
> **본 프로젝트는 iM뱅크(대구은행)의 기업 고객 데이터를 활용하여 활동성(FAI)과 수익성(FPI) 지수를 설계하고, 통계적 검증을 통해 기존 신용등급 체계에 가려진 고효율 '알짜' 고객을 발굴하는 통계 분석 기반 비즈니스 전략 프로젝트입니다.**[cite: 4]
  

  
## 1. 프로젝트 개요
- **배경** : 기존 신용등급은 부채비율, 연체율 등 '재무적 안정성'에 치중되어 있어, 성장기 중소기업의 역동적인 거래 활동이나 실제 수익 기여도를 포착하는 데 한계가 있음.  
- **목적** : 활동성 및 수익성 기반의 보완 등급 체계 제안 및 숨은 우량 고객(Hidden Star) 식별
- **기간** : 2026.03.17 ~ 2026.03.27
- **주요 성과** : 
    - FAI(활동성) 및 FPI(수익성) 하이브리드 세분화 모델 구축
    - 기존 '일반' 등급 내 고수익 알짜 타겟 고객 **12,715명** 발굴 및 프로파일링 성공
    - 비모수 검정을 통한 지수 축의 타당성 및 효율 역전 현상 통계적 입증 (p-value < 0.001)
  
  
## 2. 기술 스택

* **Language**
    <br><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=whitehttps://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">

* **Library**
    * **Data & Statistical Analysis**
        <br><img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=whitehttps://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"> <img src="https://img.shields.io/badge/Numpy-013243?style=for-the-badge&logo=numpy&logoColor=whitehttps://img.shields.io/badge/Numpy-013243?style=for-the-badge&logo=numpy&logoColor=white"> <img src="https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=whitehttps://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white"> <img src="https://img.shields.io/badge/Statsmodels-3776AB?style=for-the-badge&logo=python&logoColor=whitehttps://img.shields.io/badge/Statsmodels-3776AB?style=for-the-badge&logo=python&logoColor=white">
    * **Visualization**
        <br><img src="https://img.shields.io/badge/Matplotlib-ffffff?style=for-the-badge&logo=matplotlib&logoColor=blackhttps://img.shields.io/badge/Matplotlib-ffffff?style=for-the-badge&logo=matplotlib&logoColor=black"> <img src="https://img.shields.io/badge/Seaborn-4479A1?style=for-the-badge&logo=python&logoColor=whitehttps://img.shields.io/badge/Seaborn-4479A1?style=for-the-badge&logo=python&logoColor=white">
  
  
## 3. Data 정보
### 데이터 구성
- **규모**: iM뱅크 내부 법인 거래 데이터 및 거시 경제 지표 결합
- **분석 대상**: 0원 ~ 5,000억 원 규모의 중소기업 집단 (이상치 분리 후)

====
2. 핵심 지수 설계 (Metric Design)
모든 지표는 분포의 왜곡을 보정하기 위해 log1p 변환 후, MinMaxScaler(0~1)를 적용하여 결합되었습니다.  

📊 FAI (Financial Activity Index, 활동성 지수)
기업이 시장에서 얼마나 활발하게 움직이는지(외형적 활력)를 측정합니다.  

규모 점수: 총예금/대출 잔액, 전체 거래액, 외환/카드 사용액 기반.  

빈도 점수: 채널 거래 건수 및 외환 거래 건수 기반.  

다양성 점수: 예금, 대출, 카드, 외환 등 핵심 서비스 이용 종수 반영.  

공식: FAI = (규모 + 빈도 + 다양성) / 3

  

📈 FPI (Financial Profitability Index, 수익성 지수)
자본 대비 경영 내실과 은행 수익 기여도를 측정합니다.  

수익 기여 점수: 실질 예대마진(이자이익)과 수수료 기반 추정 비이자수익의 합.  

수익 효율 점수: 자산대비수익률(%). 총 자산 대비 발생한 영업 수익의 비율.  

공식: FPI = (수익 기여 + 수익 효율) / 2

  

3. 분석 방법론 및 통계적 검증
데이터의 왜곡(Zero-inflated, Right-skewed)을 고려하여 비모수 검정을 통해 분석의 신뢰성을 확보했습니다.  

Kruskal-Wallis H Test: 기존 등급별 FAI, FPI의 유의미한 분포 차이 확인 (p < 0.001).  

Chi-square Test: 기존 등급과 신규 사분면 모델 간의 독립성 검정 결과, 모델의 보완적 가치 입증.  

Dunn 사후검정: 동일 등급 내에서도 사분면별로 고유한 고객 특성이 존재함을 통계적으로 증명.  

4. 핵심 분석 결과 (Key Findings)
① '알짜(Cash Cow)' 그룹의 가치 발견
알짜 집단은 최상위인 '스타' 집단보다 활동 규모는 작지만, 자산 대비 수익 효율은 약 1.3배(0.47% vs 0.36%) 더 높게 나타남.  

이는 적은 자원과 활동으로도 높은 수익을 창출하는 '강소형 우량 고객'임을 시사함.  

② '효율 역전 현상'의 증명
보정 활동 수익 밀도 분석 결과, 기존 '일반' 등급의 알짜 고객이 '우수' 등급의 알짜 고객보다 더 높은 수익 효율을 보임을 확인.  

기존 등급 체계에서 저평가되었던 고효율 고객군(Hidden High-Value)의 존재를 통계적으로 입증.  

5. 비즈니스 전략 제안 (Action Plan)
타겟팅: 기존 '일반' 등급 내 숨겨진 고효익 고객 12,715명 집중 관리.  

디지털 전환(DT): 알짜 고객 중 디지털 채널 미사용 비중(61%)이 높은 고객을 대상으로 한 온보딩 유도.  

수익 다각화: 예금·대출 위주 거래 고객에게 법인카드, PG, 외환 등 비이자 수익 상품 교차 판매.  

지역 특화 지원: 대구·경북(시설자금)과 수도권(운전자금)의 상이한 니즈에 맞춘 정교한 여신 지원.
