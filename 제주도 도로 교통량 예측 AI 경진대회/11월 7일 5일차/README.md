# 오늘 한 것
eda를 마쳤다. 근데 생각보다 큰 소득이 없다. 새롭게 파생변수를 만드는 방법은 터득했는데, 어떻게 해야 더 상관관계가 높은 변수를 만들어
내는지 이런저런 인사이트를 좀 더 찾아야 겠다.

## 1. <차로수-도착지점의 위도>분석
이건 여러 범주로 이루어진로 이루어져 있었다.
![image](https://user-images.githubusercontent.com/95357946/200355966-b96f8e26-c564-46e3-a9bf-d33bb68c950b.png)
이런식으로 출력이 됨. 이건 좀;;;;

따라서 이걸 bin으로 나누어주는 걸 했다.

원래 최소, 최댓값을 잡고 분할로 할려고 했는데, 계속 결측치가 생겨서 방법을 찾던차에 이런 방법을 만들어 냈다.

```
labels = [1,2,3,4,5,6]
train_df['시작지점명 bin 6'] = pd.cut(train_df['시작지점명'],6,labels=labels)
```
이런식으로 하면 6개로 구간을 분할해서 데이터를 category 데이터로 만들어 준다.

## 2. <시작지점명-통과제한하중> -- 0.34
이것도 **<차로수-도착지점의 위도>분석**과 유사한 상황이라 구간 분할을 진행했다. 근데 두 데이터가 정수 값 자체의 유사도가 매우 높아서
상관관계가 너무 높아져 버렸다. 음... 이게 맞나...

## 히트맵
최종적인 히트맵을 만들었다. 근데 이전 히트맵과 변수 몇개를 제외하기는 했지만 별반 다를게 없어서(새로운 변수를 만들어 낸다던지)하는게
없어서 좀 허무했다. 나름 열심히 한다고 했는데, 완전히 도전하는 경진대회가 처음이라 그런가 내가 eda에서 할 수 있는건 이까지 인것 같다.

![image](https://user-images.githubusercontent.com/95357946/200358634-a25c0166-28a4-4cb7-9e35-c4d29a1c546d.png)

그리고 새롭게 알게된 사실이 있다. object형 데이터는 상관관계 분석이 안된다는 거다.

이걸 몰라서 계속 object데이터를 어떻게든 끼워볼거라고 삽질을 좀 했는데, 애초에 수치형 데이터만 상관관계 분석이 된다고 해서

```
train_df = train_df.astype({'도착지점의 위도 bin 5':'int'})
train_df = train_df.astype({'시작지점명 bin 5':'int'})
```
이런식으로 카테고리를 int로 변환해서 히트맵에 적용시켰다.

# 내일 할 것
[레퍼런스1](https://dacon.io/competitions/official/235959/codeshare/6507?page=1&dtype=recent)를 참고하면 object 데이터를 
상관관계 분석에 성공한 부분이 있다. 바로 이코드다.
```
le = LabelEncoder()
for data in datasets:
    # 범주형 -> 연속형으로 변경
    data['TypeofContact'] = le.fit_transform(data.TypeofContact)
    data['ProductPitched'] = le.fit_transform(data.ProductPitched)
    data['MaritalStatus'] = le.fit_transform(data.MaritalStatus)
    data['Designation'] = le.fit_transform(data.Designation)
    data['IncomeBin'] = le.fit_transform(data.IncomeBin)
    data['AgeBin'] = le.fit_transform(data.AgeBin)
    data['DurationBin'] = le.fit_transform(data.DurationBin)
    data['Occupation'] = le.fit_transform(data.Occupation)
    data['Gender'] = le.fit_transform(data.Gender)
    data['Children'] = le.fit_transform(data.Children)
    data['TripsBins'] = le.fit_transform(data.TripsBins)
```
내일은 transform을 사용해서 나도 히트맵을 크게 한번 더 만들어 보고 저번 레퍼런스에서 봤던 automl까지 적용해보는게 목표다. 
