시험이다 뭐다 하면서 좀 오랜 시간동안 프로젝트를 진행하지 못했다.

주말이라 시간이 좀 나서 프로젝트를 조금 진행했다.

[레퍼런스 분석1](https://github.com/stockmanager1/AI-TIL/blob/main/dacon/%EC%97%AC%ED%96%89%EC%83%81%ED%92%88%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/%EB%A0%88%ED%8D%BC%EB%9F%B0%EC%8A%A4_%EB%B6%84%EC%84%9D_1.ipynb)

# 오늘 한것
## 1. <도로유형 - 시작지점의 경도>를 분석했다.
## 2. 기본적인 변수에 대한 분석툴을 만들었다.

```
df에 데이터 프레임을 col에 해당하는 칼럼을 쓰면 해당 칼럼에 대한 히스토그렘이 만들어짐

def identify_hist(df, col):

  print(df[col].unique())

  sns.histplot(data=df[col], kde=True)
```
```
각 범주형 변수의 구성을 보여줌

def identify_count(df, col):

  print(df[col].unique())

  print(df[col].value_counts())

  sns.countplot(data=df, x=col)
  plt.show()
```

## 3. unique함수를 사용해봄

```
print(df[col].unique())
```

## 4. apply를 이용해 파생변수를 만들어봄
```
data라는 df에 children이라는 변수를 만듬. 이때 x=0은 false, 외외는 true로 출력
for data in datasets:
    data['Children'] = data.NumberOfChildrenVisiting.apply(lambda x: False if x==0.0 else True)
```
## 5. sns 소수점을 제거함.
```
from matplotlib.ticker import MaxNLocator
ax[1].xaxis.set_major_locator(MaxNLocator(integer=True))
```
## 6. 범주형 데이터를 하나하나 뜯어서 분석해봄
범주형데이터를 따로 따로 분석할때는 새로운 해당 범주에 속하는 새로운 df를 만들어 분석해야 한다.
```
df = test_df[test_df['차로수'] == 3]
fig,ax= plt.subplots(1,1,figsize=(16,9))
k = sns.histplot(data=df,x='통과제한하중',hue='차로수',kde=True);
k.set(title = '통과제한하중에 대한 차로수3의 경도 분포')
```
# 내일 할것
1. 범주형 데이터에 대해 파생변수로 만들어 저장하자.
2. 나머지 자세히 변수를 살펴볼것
3. 레퍼런스 더 분석
