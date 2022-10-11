오늘은 데이터에 대한 EDA를 시작했다.

특히 회귀 분석은 그 학습보다 데이터의 인지 및 전처리가 학습만큼 중요하기 때문에 전처리를 시작해보려고 한다.

# 오늘 한것
1. 전반적인 데이터를 불러옴.(코랩을 통해 데이터를 가지고 옴)

2. 결측치가 있는지 info를 이용해 찾아봄. 딱히 결측치는 없었다.

3. 목차가 한글화 안되어서 반복문을 통해 한글화에 성공했다.

```
for i,j in zip(test_df.columns, test_info_df['변수 설명'].iloc[0:23]):
  test_df.rename(columns={i : j},inplace=True)
```

4. 수치형 데이터와 범주형 데이터를 분리했다. 근데 시간대, 도로 등급, 차로수등은 범주형데이터에 속할것 같은데 수치형에 분류되어있다. 이걸 유념하자.

5. 일단 대략적인 상관관계 분석을 시작했다. 

```
train_corr_df=train_df.corr()
```


```
fig = plt.figure(figsize = (10,10))
sns.heatmap(train_copy_del_df.corr(), annot = True)
plt.show()

```
heatmap으로 구현해봄

근데 별로 지금의 상관관계에서는 얻을게 없었다.

6. 도로사용여부가 가장 중요해보여서 어떻게 분류가 되어있는지 체크해보았다. 

7. 게시판을 읽다가 유용한 EDA를 보았다. 바로 함수를 써서 바로 데이터의 갯수, 분포, 그래프구현까지 한번에 할 수 있는 좋은 함수가 공유되어서 한번 구현했다. 앞으로 매우 유용할 것 같다.

범주형 데이터를 각 데이터의 구성 성분을 나타내준다. 
```
def identify_count(df, col):

  print(df[col].value_counts())

  sns.countplot(data=df, x=col)
  plt.show()
```
수치형 데이터에 대해 히스토그램을 그려주는 함수다. 바로바로 쓸 수 있어서 매우 유용하다.
```
def identify_hist(df, col):

  sns.histplot(data=df[col], kde=True)
```

8. sns의 고질적인 문제인 한글 깨짐현상을 해결했다.

폰트가 설치되어 있는지 확인하는 코드

```
import matplotlib.font_manager as fm

font_list = [font.name for font in fm.fontManager.ttflist]
font_list
```
한글화 파일을 설치해주는 코드
```
%matplotlib inline  

import matplotlib as mpl 
import matplotlib.pyplot as plt 
import matplotlib.font_manager as fm  

!apt-get update -qq
!apt-get install fonts-nanum* -qq

path = '/usr/share/fonts/truetype/nanum/NanumBarunGothic.ttf' 
font_name = fm.FontProperties(fname=path, size=10).get_name()
print(font_name)
plt.rc('font', family=font_name)

fm._rebuild()
mpl.rcParams['axes.unicode_minus'] = False
```
적용하는 코드
```
plt.rc("font", family = "NanumBarunGothic")
sns.set(font="NanumBarunGothic", 
rc={"axes.unicode_minus":False}, style='white')
```

# 내일 할것
1. 모든 변수를 위에서 정의한 함수로 변환해보기

2. 범주형데이터를 각각 분리 할 수 있는 방법을 찾아보기(파생변수 만들기)

3. 다른 EDA과정 분석해보기(이거 꼭해라)

[rference1](https://dacon.io/competitions/official/235959/codeshare/6507?page=1&dtype=recent)
[reference2 여기에 age칼럼을 분리하는 부분이 나온다](https://dacon.io/competitions/official/235959/codeshare/6477?page=1&dtype=recent)
[reference3](https://dacon.io/competitions/official/235949/codeshare/6629?page=1&dtype=recent)
[reference4](https://dacon.io/competitions/official/235867/codeshare/4028?page=1&dtype=recent)
[reference5](https://dacon.io/codeshare/5768?dtype=recent)
[상관분석이란](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=sub_om&logNo=220755048371)
