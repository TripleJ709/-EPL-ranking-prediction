# **EPL 2024-25 시즌 순위 예측**

본 프로젝트는 머신러닝 기법을 활용하여 2024-25 잉글랜드 프리미어리그(EPL) 시즌의 순위를 예측하는 것을 목표로 합니다. 과거 경기 데이터를 바탕으로 미래 경기 결과를 예측하고 최종 팀 순위를 계산합니다.

---

## **목차**
1. [프로젝트 개요](#프로젝트-개요)
2. [데이터](#데이터)
3. [방법론](#방법론)
4. [결과](#결과)
5. [한계](#한계)
6. [데이터셋 출처](#데이터셋-출처)

---

## **프로젝트 개요**
이 프로젝트의 주요 목표는 다음과 같습니다:
- 머신러닝을 활용하여 과거 경기 데이터를 분석.
- 2024-25 시즌 EPL 경기 결과를 예측하고 팀 순위를 도출.
  
---

## **데이터**
### **사용된 데이터셋**
- **1993-94 ~ 2021-22 시즌 경기 결과** : `results.csv`
- **2022-2023 시즌 경기 결과** (2022-23): `Since2023.csv`
- **2023-24 시즌 경기 결과**: `League24.csv`
- **2024-25 시즌 경기 일정**: `League25.csv`

### **주요 변수**
- `Home`, `Away`: 홈팀과 원정팀 이름.
- `HomeGoals`, `AwayGoals`: 홈팀과 원정팀의 득점 수.
- `FTR` (Full-Time Result): 경기 결과 (홈 승리(H), 무승부(D), 원정 승리(A)).
- `Season_End_Year`: 시즌 종료 연도.

---

## **방법론**
### **1. 데이터 전처리**
- 모든 CSV 파일의 형식을 통일.
- `team_name_mapping`을 통해 팀 이름 매핑.

### **2. 모델 구성**
- **신경망 설계**:
  - 3개의 은닉층과 배치 정규화, 드롭아웃 적용.
  - Softmax 활성화 함수로 다중 클래스 분류.
- **입력 변수**:
  - 시즌 종료 연도, 팀 이름(숫자로 매핑), 홈/원정 승률, 골 차이.
- **출력 변수**:
  - `FTR` (H, D, A로 표시된 경기 결과).

### **3. 학습**
- 5-fold 교차 검증(Cross-Validation)을 사용해 모델 성능 향상.
- EarlyStopping으로 과적합 방지.
- 클래스 가중치로 데이터 불균형 문제 해결.

---

## **결과**
- **모델 성능**:
  - 모든 fold에서 높은 정확도를 달성.
  - 가장 성능이 좋은 모델을 최종적으로 사용.
- **2024-25 시즌 예측**:
  - **우승팀**: Arsenal.
  - **강등팀**: Wolves, Bournemouth, Brentford.
- **시각화**:
  - 팀 순위 막대 그래프.
  - 경기별 팀 승점 변화 그래프.

![Points Progression](path/to/points_progression_image.png)

---


### **한계**
- 외부 요인(부상, 이적, 전술 변화 등)을 반영하지 못함.
- 모델의 예측에서 팀 간 승점 차이가 실제보다 큼.

---

## 데이터셋 출처
- [EPL 경기 결과 데이터셋 (Kaggle)](https://www.kaggle.com/datasets/irkaal/english-premier-league-results)
- [1992-2022 프리미어리그 경기 데이터](https://www.kaggle.com/datasets/evangower/premier-league-matches-19922022)
- [2023-24 시즌 데이터](https://www.kaggle.com/datasets/danilocardoso/premier-league-20232024)
- [EPL 24-25 데이터 분석](https://www.kaggle.com/code/meraxes10/basic-analysis-on-epl-24-25-data)



