# 🚨 온라인 정신건강 위기 '약신호(Weak Signal)' 탐지 파이프라인
*(Detecting Weak Signals of Mental Health Crises via 7-Stage NLP Pipeline)*

<p align="left">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=Python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=Jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/NLP-Natural_Language_Processing-success?style=flat-square"/>
  <img src="https://img.shields.io/badge/Data_Analysis-Public_Safety-blue?style=flat-square"/>
</p>

## 📌 Project Overview (프로젝트 개요)
본 프로젝트는 사후 개입 위주의 기존 치안 및 공공보건 시스템을 선제적 예방 모델로 전환하기 위해 기획된 **데이터 분석 파이프라인 초기 모델**입니다. 

온라인 담론 내에 내재된 정신건강 위기(병리, 분노, 경계선 범죄 등)의 '약신호(Weak Signal)'를 조기에 탐지하고, 이를 실제 공공 행정 통계와 교차 검증하여 정책적 효용성을 입증하는 것을 목표로 합니다. 궁극적으로는 경찰관 및 실무자를 위한 데이터 기반 의사결정 지원 시스템(예: '모두의 경찰관' 등 치안 행정 LLM의 후속 R&D)의 기반 기술로 활용될 수 있도록 7단계의 모듈화된 프로세스로 설계되었습니다.

## ⚙️ 7-Stage Pipeline Architecture (7단계 분석 프로세스)

| 단계 | 프로세스명 | 핵심 내용 |
| :---: | :--- | :--- |
| **01** | `Data Collection` | 3대 전조증상(병리, 분노, 경계선 범죄) 키워드 기반 네이버 뉴스 텍스트 크롤링 |
| **02** | `Clinical Preprocessing` | DSM-5-TR 임상 진단 기준 사전을 적용한 비정형 텍스트 정제 및 형태소 분석 |
| **03** | `Index Calculation` | 단어빈도(TF), 문서빈도(DF) 및 시간가중 가시성(DoV)·확산성(DoD) 지표 산출 |
| **04** | `KEM-KIM Filtering` | KEM-KIM 2사분면(진성 약신호) 도출 및 비일관적 노이즈(단발성 이슈) 필터링 |
| **05** | `SNA & LDA Modeling` | 진성 약신호 대상 의미연결망(SNA) 매개 중심성 연산 및 LDA 토픽 모델링 |
| **06** | `Visualization & Report` | 다차원 시각화(Topic Trend & SNA), 최종 리포트 생성 및 7단계용 월별 트렌드 추출 |
| **07** | `Public Data Cross-Validation`| 6단계 추출 트렌드와 공공 통계(HIRA 건강보험, KOSIS 자살률 등) 간 시차 교차 상관관계(Cross-Correlation) 검증 |

## 📂 Repository Structure (폴더 구조)
본 레포지토리는 파이프라인의 데이터 흐름에 따라 순차적으로 구성되어 있습니다.

```text
├── 01_Data_Collection/
├── 02_Clinical_Preprocessing/
├── 03_Index_Calculation/
├── 04_KEM_KIM_Filtering/
├── 05_SNA_LDA_Modeling/
├── 06_Visualization_and_Report/
├── 07_Public_Data_Cross_Validation/
└── README.md
