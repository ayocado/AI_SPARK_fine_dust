# <a href="https://aifactory.space/competition/detail/2317" target="_blank">제5회 2023 연구개발특구 AI SPARK 챌린지 - 사회문제해결형</a>
## 🚩 대회 정보
- 주제 : 초미세먼지(PM2.5) 오염도 단기 예측 모델 만들기
- 기간 : 23.04.24 ~ 23.05.11
- 결과 : 48위 / 118팀 (8.41651929점)
<br>

## 🎈 대회 주제 소개
##### 지역사회 대기오염 예측 인공지능 모델 개발
- 대전·세종·충남 지역 초미세먼지(PM2.5) 오염도를 시간단위로 예측하는 모델을 만드는 것이 본 과제의 목표입니다.
- 데이터의 연도/시간/값은 비식별화 되어있습니다.
- 데이터의 위치는 다음과 같습니다. (청색: AWS 측정소 / 적색: PM2.5 측정소)
<br>

## 📑 데이터
```
📁 dataset.zip
 ├--- 📁 TRAIN                      --- 학습용 PM2.5 데이터
 ├--- 📁 TRAIN_AWS                  --- 학습용 기상조건 데이터
 ├--- 📁 TEST_INPUT                 --- 평가용 PM2.5 데이터
 ├--- 📁 TEST_AWS                   --- 평가용 기상조건 데이터
 ├--- 📁 META                       --- PM2.5 관측소 및 AWS관측소 위치정보
 └--- 📃 answer_sample.csv          --- 정답 양식 파일
 ```
- TRAIN: 각 PM2.5 관측소별 학습용 데이터입니다. 가동 시점 및 운영 상황에 따라 결측치를 포함하고 있습니다.
- TRAIN_AWS: 각 AWS 관측소별 학습용 데이터입니다. 가동 시점 및 운영 상황에 따라 결측치를 포함하고 있습니다.
- TEST_INPUT: 각 PM2.5 관측소별 평가용 입력데이터입니다. 예측대상이 되는 시점값은 결측으로 비어있습니다. 
                        입력 대상이 되는 시점값에는 결측이 없습니다.
- TEST_AWS: 각 AWS 관측소별 평가용 입력데이터입니다. PM2.5 예측대상이 되는 시점에 대한 값은 결측으로 비어있습니다. 
                     (예측 수행 시점에 존재하지 않는 정보를 이용한 예측은 불가)
                      입력 대상이 되는 시점값에는 결측이 없습니다.
- META: 본 과제에 사용되는 PM2.5 및 AWS 관측소에 대한 위경도 정보 및 주소가 포함되어 있습니다.
- answer_sample: TEST_INPUT에 대하여 작성할 제출용 레이블 파일 양식입니다. 전체 관측소에 대한 예측을 하나의 파일에 양식대로 기재합니다.
<br>

## 📈 AI 모델링
- 결측치 처리 : KNN Imputer
- 관측소 데이터 값 : 거리에 반비례 (가까울수록 높은 영향)
- modeling 1~2 : LSTM, 구조 변경
- modeling 3~4 : CatBoost, 변수 추가(1hour, 2hour, 24hour), 거리 가중치, optuna 적용
- modeling 5~7 : LSTM, 변수 추가(dummies, 24hour, notime)
- modeling 8~9 : AutoEncoder
<br>

## 💻 기술 스택
<b> 언어 </b><br>
<span><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=Python&logoColor=white"></span><br>

<b> 라이브러리 </b><br>
<span><img src="https://img.shields.io/badge/numpy-013243?style=for-the-badge&logo=numpy&logoColor=white"></span>
<span><img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"></span>
<span><img src="https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white"></span>
<span><img src="https://img.shields.io/badge/tensorflow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white"></span><br>

<b> 프로그래밍 인터페이스 </b><br>
<span><img src="https://img.shields.io/badge/googlecolab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white"></span>
