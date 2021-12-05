# Dacon 대회 기록

## 1. 시스템 품질 변화로 인한 사용자 불편 예지 AI 경진대회
## 2. 전력사용량 예측 AI 경진대회

평가 산식 : SMAPE(Symmetric Mean Absolute Precentage Error)

1. 60 개의 건물의 전력을 날씨로 예측하는 문제였고 각 건물마다 평균과 분산이 다르다는 것을 알게 되었습니다. 그래서 저는 60 개의 건물을 각 모델에 돌리는 방식으로 SMAPE 을 낮췄습니다.
2. 6~8 월의 데이터를 가지고 분석을 진행함으로 여름에 에어컨과 선풍기 사용량이 늘어나면서 전력이 늘어날 것이라고 예상했고 사용량을 예측하는 방식으로는 불쾌지수, 열 지수를 사용했습니다.
3. 건물들의 특징으로는 주말과 평일에 차이가 심하게 나는 건물은 시간으로 구간을 정해주어 전처리를 더 구체적으로 하려고 노력했습니다.
4. 모델은 stacking 을 사용하여 xgboost, lightgbm, catboost, radomforest, ridge 예측을 한 이후에 meta model 로는 LinearRegression 을 사용했습니다.
5. 모델을 핚번 돌린 이후에 y_pred 를 target 이란 변수로 넣어주고 train 의 target 과 test 의 target 을 가지고 이동평균을 만들어서 avg_column 으로 넣어주고 다시 stacking 을 사용했습니다.
6. 이동 평균을 사용핚 이후 6 점대로 떨어지게 되었으며 49 등의 기록으로 대회를 마무리 했습니다.
