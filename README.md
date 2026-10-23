Raman Spectrum Baseline Correction & Analysis Tool 🧬📊

라만 분광 데이터전처리 및 기준선 보정, 시료 간 스펙트럼 비교와 피크 분석을 자동화하는 통합 데스크톱 GUI 애플리케이션

📌 Overview

라만 분광(Raman Spectroscopy) 데이터 분석 시 필수적인 ROI 평균화, 형광 전경 기준선 보정(Baseline Correction), 시료 간 스펙트럼 대조, 피크 검출 및 DB 검색을 단일 워크플로우로 통합한 Python 기반 도구입니다.

반복적인 CSV 데이터 처리 및 분석 단계를 하나의 GUI 환경으로 통합하여 연구 효율성을 대폭 개선했습니다.

📸 Key Features & Demo

1. ROI Data Averaging & Baseline Correction (ZhangFit)

자동 ROI 추출 & 평균화: CSV 파일에서 라만 축(Wavelength)과 여러 ROI 열을 읽어 신호 평균 스펙트럼 생성

ZhangFit 기준선 보정: BaselineRemoval 라이브러리의 Adaptive Smoothness Penalty 기반 ZhangFit 알고리즘을 적용하여 형광 배경 잡음 제거

<img width="1600" height="1000" alt="raman_real_data_baseline" src="https://github.com/user-attachments/assets/2690eefe-37c3-404a-8572-47e7fc10f8c0" />

▲ 단일/다중 CSV 파일의 Raw 스펙트럼(Blue)과 ZhangFit 보정 스펙트럼(Red) 실시간 비교

2. Multi-Sample Spectrum Comparison & Difference Analysis

스펙트럼 중첩 비교: 보정된 두 시료 스펙트럼을 동일 축 상에 시각화

정량적 스펙트럼 차이 계산: Wavelength별 신호 차이값($Difference = File_1 - File_2$)을 실시간 연산하여 인터랙티브 테이블에 출력

자동 Peak Detection: scipy.signal.find_peaks 알고리즘과 Prominence 기준 정밀 피크 탐지 (그래프 상 그린 마커로 시각화)

<img width="1600" height="1000" alt="raman_real_data_comparison" src="https://github.com/user-attachments/assets/dab84f02-94e0-4961-ada5-7c2a938b9121" />

▲ 두 시료 스펙트럼 비교, 차이값 검색 테이블 및 검출 피크 시각화

3. Interactive GUI Workflow

전체 분석 흐름을 한곳에서 수행할 수 있는 탭(Tab) 기반 멀티뷰 UI 지원

<img width="1280" height="800" alt="raman_real_data_demo" src="https://github.com/user-attachments/assets/036d3887-2bea-4b16-b4f9-59dc86aba13a" />


▲ 파일 로딩부터 기준선 보정, 스펙트럼 대조 및 차이 분석 전체 작동 데모

⚙️ Architecture & Data Pipeline

전체 데이터 처리 및 알고리즘 수행 파이프라인은 아래와 같습니다:

[Raw CSV Input] 
       │
       ▼
1. Data Preprocessing
   ├── Raman Axis (Column 1) Extraction
   └── Multi-ROI Columns Averaging ➔ Single Signal Curve
       │
       ▼
2. Baseline Correction (ZhangFit)
   └── Remove Background Fluorescence Noise
       │
       ▼
3. Interactive Analysis
   ├── Dual-Sample Overlaid Visualization (PyQtGraph)
   ├── Point-wise Difference Calculation (File 1 - File 2)
   ├── Peak Detection (scipy.signal.find_peaks + Prominence)
   └── Peak DB Lookup (XLSX Table Search by Raman Shift Range)


🛠 Tech Stack

GUI & Visualization: PyQt5, PyQtGraph

Data Processing: pandas, NumPy

Algorithm & Signal Processing: BaselineRemoval (ZhangFit), SciPy (scipy.signal)

🚀 Getting Started


git clone https://github.com/degull/raman_print-baseline_edit.git
cd raman_print-baseline_edit


Installation

필요한 라이브러리를 설치합니다:

pip install pyqt5 pyqtgraph pandas numpy scipy BaselineRemoval openpyxl


Running the Application

python main.py
