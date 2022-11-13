# 진행 코드
https://colab.research.google.com/drive/1alYXPQ5bOQ5KRtIp5bP4ToHWuyanDSdn

# 목표
1. 나만의 EDA분석툴을 만들어 본다. 이전에 대회 코드 분석([여행상품경진대회](https://github.com/stockmanager1/AI-TIL/tree/main/dacon/%EC%97%AC%ED%96%89%EC%83%81%ED%92%88%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C))을 통해서 몇가지 인사이트를 얻은 것이 있지만 좀 더 구체화시켜 바로바로 분석할 수 있는 나만의 툴을 만든다.

2. automl을 구동시켜본다. 저번에 한번 해본적이 있기는 한데 한번 다시 복습겸 해보려고 한다.

3. xgboost,catboost를 구현해보려고 한다. 저번 대회 우승자가 이걸 사용했던데, 내가 한번 공부해보고 구현해 보려고 한다.

# 일정
|일정|구체사항|
|------|---|
|2022-10-11|[EDA 1일차](https://github.com/stockmanager1/toy-project/tree/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/10%EC%9B%94%2011%EC%9D%BC%201%EC%9D%BC%EC%B0%A8)|
|2022-10-22|[EDA 2일차](https://github.com/stockmanager1/toy-project/blob/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/10%EC%9B%94%2022%EC%9D%BC%202%EC%9D%BC%EC%B0%A8/README.md)|
|2022-11-01|[EDA 3일차](https://github.com/stockmanager1/AI-TIL/tree/main/dacon/%5B%EC%B6%A9%EB%82%A8%EB%8C%80%ED%95%99%EA%B5%90%5D%20%ED%83%9C%EC%96%91%EA%B4%91%20%EB%B0%9C%EC%A0%84%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C)|
|2022-11-02|[EDA 4일차](https://github.com/stockmanager1/toy-project/tree/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/11%EC%9B%94%202%EC%9D%BC%204%EC%9D%BC%EC%B0%A8)|
|2022-11-07|[EDA 5일차](https://github.com/stockmanager1/toy-project/tree/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/11%EC%9B%94%207%EC%9D%BC%205%EC%9D%BC%EC%B0%A8)|
|2022-11-08|[모델링 6일차](https://github.com/stockmanager1/toy-project/blob/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/11%EC%9B%948%EC%9D%BC6%EC%9D%BC%EC%B0%A8/README.md)|
|2022-11-09|[모델링 7일차](https://github.com/stockmanager1/toy-project/tree/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/11%EC%9B%94%209%EC%9D%BC%207%EC%9D%BC%EC%B0%A8)|
|2022-11-10|[모델링 8일차](https://github.com/stockmanager1/toy-project/tree/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/11%EC%9B%94%2010%EC%9D%BC%208%EC%9D%BC%EC%B0%A8)|
|2022-11-11|[모델링 9일차](https://github.com/stockmanager1/toy-project/tree/main/%EC%A0%9C%EC%A3%BC%EB%8F%84%20%EB%8F%84%EB%A1%9C%20%EA%B5%90%ED%86%B5%EB%9F%89%20%EC%98%88%EC%B8%A1%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/11%EC%9B%94%2011%EC%9D%BC%209%EC%9D%BC%EC%B0%A8)|

# 결과

private 458등/708

그래도 나름 열심히 한다고 했는데, 중간에 시험에다가 automl 오류를 해결한다고 거의 대회 자체에는 신경을 못썼더니, 그렇게 좋은 결과는 내지 못했다.

처음으로 처음부터 끝까지 해본 대회고 이 경험을 기반으로 다른 여러 대회도 본격적으로 준비해보려고 한다.

## 알게된것

1.pycaret에 대해 좀 더 알게 되었다. 원래는 단순히 자동으로 돌아가는 프로그램정도로 인식하고 있었는데, 이런 저런 여러 기능들에 대해 알게 되었다. 

2.파생변수들을 새롭게 만들어 보았다.

3. train_df에서 1점대가 나왔다고 해서, 대회의 test_df target 값에서도 1점대가 나오는 건 아니다. 오히려 이때 20점나옴... 반면 train_df에서 예측 점수가 5점대지만, 대회에서 10점대가 나왔다.

4. 데이콘은 test_df에 대해 target에 대해 target값을 안준다.

5. 모델을 만들고, plot_model을 사용해서 모델을 시각화 할 수 있다. 이때 0에 가까워야 한다. 하지만 나는 쓰레기같은 결과가 나옴.
![image](https://user-images.githubusercontent.com/95357946/201528679-093ff25a-1002-4cf7-9657-ce254eb9cc4b.png)

6. pycaret으로 만드는 모델은 생각보다 성능이 너무 떨어진다. 내가 직점 만들어야함. 생각보다 너무 쓰레기라서 놀랐다. pycaret에서 얻을 수 있는건 모델비교랑, importance정도라고 생각한다.

7. 제출방법을 정확하게 알게됨. 앞으로 어떻게 준비해야 하는지 알게됨.

8. 모델 eda에 대한 툴을 어느정도 만들어 냄. 기본적인 baseline을 잡음.


8. regression에 대해 어느정도의 baseline이 잡힘.


## 목표.

처음에 나는

1. 나만의 EDA분석툴을 만들어 본다. 이전에 대회 코드 분석([여행상품경진대회](https://github.com/stockmanager1/AI-TIL/tree/main/dacon/%EC%97%AC%ED%96%89%EC%83%81%ED%92%88%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C))을 통해서 몇가지 인사이트를 얻은 것이 있지만 좀 더 구체화시켜 바로바로 분석할 수 있는 나만의 툴을 만든다.

2. automl을 구동시켜본다. 저번에 한번 해본적이 있기는 한데 한번 다시 복습겸 해보려고 한다.

3. xgboost,catboost를 구현해보려고 한다. 저번 대회 우승자가 이걸 사용했던데, 내가 한번 공부해보고 구현해 보려고 한다.

의 목표를 이루려고 했다.

1. 나만의 회귀 baseline의 틀을 잡았다. 내일 바로 정리해서 커밋할려고 한다.

2. automl중 pycaret을 구동해보고 좀 더 알아야 겠다는 것을 알게됨.

3. xgboost는 구현해보았다. 하지만 catboost는 구현해보지 못했다.

## 결론

첫 데이콘 대회라 여러 부분에서 버벅거려 시간을 많이 잡아 먹었다. 다음에는 빨리, 그리고 자주 관심을 가져야 겠다.
