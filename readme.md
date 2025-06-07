# 기출 정리

## 1과목
#### 헷갈리는거 정리
1. .isin([]),  in () , .str.contains()<br>
    * .isin([]) - series에 대해 여러 값을 비교할 때
    ~~~
    df['컬럼명'].isin(['A', 'B', 'C'])
    #해당 list에 존재하는 열만 필터링
    ~~~
    * .str.contains() - series에서 특정 문자열 포함 여부
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
4. pivot<br>
unstack과 pivot의 차이가 뭘까?<br>
둘다 dataframe을 넓게(pivot) 바꾸는 데 쓰임<br>

    * unstack() : 보통 groupby+unstack() 함께 사용됨<br>
        * 전제: multiIndex 되어있어야함
        * 목적: index레벨을 columns으로 이동
        * 집계 기능: 없용
        * 중복값 허용 X
        
    * pivot_table()
        * 전제: 일반 dataframe
        * 목적: 원하는 행/열 기준으로 집계된 table 생성
        * 집계 기능: aggfunc으로 가능
        * 중복값 허용

5. iloc vs loc

6. str 함수들
~~~
.str.startswith('') # 특정 문자로 시작하는거
.str.len() #단어수 구하기 
~~~

7. groupby
~~~
groupby([]).특정컬럼.agg(['mean', 'var', 'max', 'min']) #agg함수 많이 사용됨
groubpy([], as_index=False) #as_index=False하면 새로운 인덱스 만들어지고 column자체가 index화 되지 않음
groupby([multi]).연산.unstack() #pivot화, 이거는 multiIndex일 때 뒤에 columns이 table의 columns화
groupby().연산.to_frame() # dataframe으로 만들기

#부가적으로 어렵다고 생각했던 연습문제
temp = df.groupby(['neighbourhood_group']).room_type.value_counts().unstack()
temp.loc[:,:] = temp.values/temp.sum(axis=1).values.reshape(-1,1)

~~~

8. apply, map
* map - 1:1 mapping이 필요할 때
~~~
category = {
    'Unknown' : 'N',
    'Less than $40K' : 'a',
    '$40K - $60K' : 'b',
    '$60K - $80K' : 'c',
    "$80K - $120K" : "d",
    '$120K +' : 'e'
}
df['Income_Category'] = df['Income_Category'].map(lambda x: category[x])
~~~

* apply - 함수를 적용해야할 때
~~~
df['newEduLevel'] = df['Education_Level'].apply(lambda x: 1 if 'Graduate' in x else 0)
~~~

9. time_series

10. merge, concat



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
