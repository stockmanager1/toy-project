# 오늘 한것
1. xbboost 적용 - no tune
2. lightgbm 적용 - no tune
3. automl로 최적화를 찾아서 randomforest 적용 -no tune
4. xgboost gridsearch 대강 적용 -little tune

이번에 처음으로 lightgbm을 스스로 모델링을 해봤다.

# 결과 
1. xgboost - score 56.921157929	
2. lightgbm - score 57.5093127912	
3. automl로 최적화를 찾아서 randomforest 적용 score 62.4332085293
4. xgboost gridsearch 대강 적용 score **56.3351353951**

# 내일 해야 하는 것
즉 xgboost를 좀 더 튜닝을 해보는 방향으로 잡아보자. [레퍼런스](https://kimginam1995.tistory.com/628)

튜닝을 조금 더 복잡하게 해서 적당한 모델이 나온다면, 이때 범주형 데이터에 대해 스케일링을 해보자.



