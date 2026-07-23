# 🚨 온라인 정신건강 위기 '약신호(Weak Signal)' 탐지 파이프라인
*(Detecting Weak Signals of Mental Health Crises via Modular 6-Stage NLP & CCF Pipeline)*

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=Python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=Jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/NLP-Natural_Language_Processing-success?style=flat-square"/>
  <img src="https://img.shields.io/badge/Data_Analysis-Public_Safety-blue?style=flat-square"/>
</p>

## 📌 Project Overview (프로젝트 개요)
본 프로젝트는 사후 개입 위주의 기존 치안 및 공공보건 시스템을 선제적 예방 모델로 전환하기 위해 기획된 **데이터 분석 파이프라인 모델**입니다. 

온라인 담론 내에 내재된 이상동기 범죄(Abnormal Motive Crimes) 및 정신건강 위기의 '약신호(Weak Signal)'를 조기에 탐지하고, 대중 여론(댓글)이 공식 담론(뉴스 기사)에 선행한다는 사회학적 가설(H1)을 시차교차상관(CCF) 통계 분석으로 검증하는 것을 목표로 합니다. 궁극적으로는 경찰관 및 실무자를 위한 데이터 기반 의사결정 지원 시스템(예: '모두의 경찰관' 등 치안 행정 LLM의 후속 R&D)의 기반 기술로 활용됩니다.

## ⚙️ 6-Stage Pipeline Architecture (6단계 분석 프로세스)

| 단계 | 프로세스명 (파일명) | 핵심 내용 |
| :---: | :--- | :--- |
| **01** | `Dual Data Collection` | 3대 전조증상 키워드 기반 네이버 뉴스 기사 및 댓글 텍스트 듀얼 크롤링 |
| **02** | `Clinical Preprocessing` | 정규식 및 형태소 분석(Kiwi)을 통한 비정형 텍스트 정제 및 토큰화 |
| **03** | `LDA Topic Modeling` | 잠재 Dirichlet 할당법을 활용한 시계열 구간별 위기 담론 토픽 비중 변화 분석 |
| **04** | `KEM/KIM Filtering` | 시간가중치($tw=0.05$) 및 중앙값 기준 사분면 맵핑, 시계 방향 진화 패턴을 통한 비일관적 노이즈(단발성 이슈) 필터링 |
| **05** | `SNA & Hub Extraction` | 진성 약신호 대상 의미연결망(SNA) 중심성(연결정도·매개) 연산 및 핵심 뇌관(Hub) 월별 트렌드 추출 |
| **06** | `CCF Statistical Validation` | 동일 키워드의 대중 여론(댓글)-공식 담론(기사) DoV 시계열 간 **시차교차상관(Lagged CCF) 분석을 통한 선행성(H1) 통계 검증** |

## 📂 Repository Structure (폴더 구조)
본 레포지토리는 모듈화된 독립 실행형 파이프라인의 데이터 흐름에 따라 순차적으로 구성되어 있습니다.

```text
├── 01_Data_Collection/              # 뉴스 기사 및 댓글 수집 스크립트
├── 02_Clinical_Preprocessing/       # 텍스트 정제 및 토큰화 (`_preprocessed.csv`)
├── 03_LDA_Topic_Modeling/           # 토픽 모델링 및 트렌드 추출
├── 04_KEM_KIM_Filtering/            # KEM/KIM 지표 산출 및 비일관성 필터링 (`_kem_kim_matrix.csv`)
├── 05_SNA_and_Hub_Extraction/       # SNA 중심성 분석 및 월별 뇌관 트렌드 도출 (`_hub_monthly_trends.csv`)
├── 06_CCF_Statistical_Validation/   # 시차교차상관(CCF) 분석 및 가설(H1) 검증 모듈
└── README.md
