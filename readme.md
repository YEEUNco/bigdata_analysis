# 기출 정리

### 기출 2회차 
---
### 기출 3회차
---
### 기출 4회차
---
### 기출 5회차
처음으로 회귀문제가 나옴
RandomForestRegressor 사용만 다르지 똑같음

평가지표로 RMSE 
~~~
from sklearn.metrics import mean_squared_error
from numpy as np

np.sqrt(mean_squared_error(x_test, pred))
~~~
즉, 한번에 평가지표를 구할 수 없음

그리고 error는 작을 수록 좋은 것

---
### 기출 6회차
test의 범주형 변수와 train의 범주형 변수의 수가 맞지 않음<br>
-> 이런 경우는 get_dummies하고 randomforest에 넣으면 error발생

해결 방안<br>
1. 해당 컬럼 drop
2. col의 순서가 맞지 않다면 test_pred = test_pred[list(x.columns)]<br>

참고
* randomforest는 column의 순서 중요!!

---
### 기출 7회차
조금 색달랐던게 날짜 데이터가 처음으로 등장
randomforest, xgboost 모두 int만 처리할 수 있음으로 파생변수를 만들어서 처리

---
### 기출 8회차


---
### 기출 9회차

