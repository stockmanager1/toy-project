
# 일정
|일정|구체사항|
|------|---|
|2022-12-26|[EDA 1일차](https://github.com/stockmanager1/toy-project/tree/main/%EC%9C%A0%EC%A0%84%EC%B2%B4%20%EC%A0%95%EB%B3%B4%20%ED%92%88%EC%A2%85%20%EB%B6%84%EB%A5%98%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/12%EC%9B%94%2026%EC%9D%BC%201%EC%9D%BC%EC%B0%A8)|
|2022-12-27|[가설 수립 및 실험 진행 1일](https://github.com/stockmanager1/toy-project/tree/main/%EC%9C%A0%EC%A0%84%EC%B2%B4%20%EC%A0%95%EB%B3%B4%20%ED%92%88%EC%A2%85%20%EB%B6%84%EB%A5%98%20AI%20%EA%B2%BD%EC%A7%84%EB%8C%80%ED%9A%8C/12%EC%9B%94%2027%EC%9D%BC%202%EC%9D%BC%EC%B0%A8)|

# eda 결과

1. 부모 변수와 성 변수는 단일변수로 아무런 영향을 끼치지 않는다. 즉 삭제한다.

![image](https://user-images.githubusercontent.com/95357946/209654034-7c246eef-ec25-49e4-8b25-91a58bcce9d0.png)

2. 피어슨 상관계수에 따르면, snp_1,3,5,8,10이 서로 연관성이 뛰어나고, snp_2,4,6,7,9,11,12,13,14,15가 서로 상관관계가 깊다.

3. snp_1,3,5,8,10 그룹이 target,trait와 밀접한 연관을 보인다.

4. snp _2,4,6,7,11,12,13,14,15는 target,trait와 상관관계가 음을 보인다.

5. trait과 target의 상관관계는 변수들의 상관관계 중 가장 높다.

6. 하지만 trait은 1에만 tartget-a를 가지고, 2에는 target-b,c를 가진다.

7. 총 유전 형질은 gg,ag,aa,ca,cc,ga로 총 6가지가 존재한다.

# 가설 수립(더 좋을 생각이 있더면 차차 보완할 예정)

1. target과 상관관계가 높은 sp_1,3,5,8,10을 더미변수로 만든다.

2. target과 상관관계가 낮은 snp_2,4,6,7,9,11,12,13,14,15를 더미변수로 만든다.

3. 모두 더미변수로 만들어 본다.

4. trait가 가장 상관관계가 높으므로, 이것만 더미변수로 만들어 본다.

5. snp상관없이 해당열에 aa,ag등이 몇개인지 칼럼을 만든다. + 기존변수 유지

6. snp상관없이 해당열에 aa,ag등이 몇개인지 칼럼을 만든다. + 기존변수 삭제


