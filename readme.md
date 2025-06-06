# 기출 정리

## 1과목
#### 헷갈리는거 정리
1. .isin([]),  in () , .str.contains()<br>
    * .isin([]) - series에 대해 여러 값을 비교할 때
    ~~~
    df['컬럼명'].isin(['A', 'B', 'C'])
    #해당 list에 존재하는 열만 필터링
    ~~~
    * .str.contains() - series에서 특정 문자열 포함 여링
    ~~~
    df[df['상품명'].str.contains('apple')]
    #apple이 포함되어있는 row 필터링
    ~~~
    * in [] - 특정 원소가 리스트, 문자열, 딕셔너리 등에 포함되는지 확인
    ~~~
    '사과' in ['사과', '귤'] # return true
    ~~~

2. drop_duplicates('특정열 기준으로', keep=''), dropna()
* drop_duplicates
~~~
df.drop_duplicates('특정열', keep='last') #마지막꺼 남기기
df.drop_duplicates('특정열', keep='first') #앞에꺼 남기기
df.drop_duplicates('특정열', keep=False) #모든 열 지우기
~~~
* dropna()
~~~
df.drop(axis=0) #default
df.drop(axis=1)
df.drop(how='all') #전체 na인 행만 삭제
df.drop(subset=['A','B']) # A 또는 B열이 na이면 삭제
~~~
3. std()
* 모표준편차
~~~
.std(ddof=0)
~~~
* 표본표준편차(default)
~~~
.std(ddof=1)
.std()
~~~
4. pivot_table


## 2과목

#### 기출 2회차 
---
#### 기출 3회차
---
#### 기출 4회차
---
#### 기출 5회차
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
#### 기출 6회차
test의 범주형 변수와 train의 범주형 변수의 수가 맞지 않음<br>
-> 이런 경우는 get_dummies하고 randomforest에 넣으면 error발생

해결 방안<br>
1. 해당 컬럼 drop
2. col의 순서가 맞지 않다면 test_pred = test_pred[list(x.columns)]<br>

참고
* randomforest는 column의 순서 중요!!

---
#### 기출 7회차
조금 색달랐던게 날짜 데이터가 처음으로 등장
randomforest, xgboost 모두 int만 처리할 수 있음으로 파생변수를 만들어서 처리

---
#### 기출 8회차
급 전처리 해야할 것들이 는 느낌? - 아닌 거 같기도?<br>
처음에는 그렇게 보였는데 그냥 하면 된다

새로운 평가지표 mae - mean_absolute_error

---
#### 기출 9회차
가장 normal했다
