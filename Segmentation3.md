## Customer-segmentation-and-consumer-behavior-analysis ##

80/20 rule (Pareto principle)- 파레토법칙

Topic1

 - 구매 행동을 기준으로 소비자 세그먼트
k-means clustering algorithm 사용
Elbow method 이용 optimal number of segments: 3
 - k-means 결과 3개의 segments로 분류
1. channel과 region을 dummy로 만들어서 segment별 분류
==> majority of customers are from Channel 2 / Region 3
dummy로 만드는 이유 생각해보기

REGION Frequency
Lisbon 77
Oporto 47
Other Region 316
Total 440

CHANNEL Frequency
Horeca 298
Retail 142
Total 440

scikit-learn은 문자열 값을 입력값으로 허락하지 않기 때문에 숫자형으로 인코딩
하지만, 1, 2, 3 같이 변경하고 예측하면 잘못된 관계를 형성할 수 있음
⇒ 고유 값의 개수만큼 컬럼 만들어 예측


2. Product별 분류
==> product별로 주요 segment가 다름



Topic2
 - top 20% 의 customer/products/geographic location이 80%의 수익 창출

1. customer ID별로 Revenue 총합 도출 
customer ID의 top 25%(4334명 중 1084명)의 Revenue 총합을 구하면 전체 Revenue의 79%가 도출 됨 
(하지만 retail industry의 특성상 나머지 75% customer도 추후에 target이 될 수 있음을 배제하면 X)

2.  product별로 Revenue 총합 도출
products의 top 20%(3877개 중 775개)의 Revenue 총합을 구하면 전체 Revenue의 79%

3.   country별로 Revenue 총합 도출
top 10 countries를 시각화하면 UK가 압도적. 
bottom 10 countries 확인(why...?)
UK 한 국가가 82%의 Revenue 창출

----------

##House Price Prediction##

Using Linear Regression Model

변수 6개
Avg. Area Income	
Avg. Area House Age	
Avg. Area Number of Rooms	
Avg. Area Number of Bedrooms	
Area Population	
Price

1. EDA 작업을 통해 
- 변수들간의 관계 파악(pair plot/heatmap)
- price 변수의 분포 확인(distplot)

2. x/y array 나누기 
- price가 y 축(target variable)이 됨
- 나머지가 x축(independent variable)이 됨
 
3. Train/Test data로 나누기
 
4. sklearn의 linear regression을 이용해 학습시킴
- lm= LinearRegression() 
- lm.fit(X_train, y_train)

5. coefficients(계수) 확인
- 1 unit이 증가하면 각 독립변수가 증가하는 수치

6.  모델 예측
- prediction = lm.predict(X_test)
- plt.scatter(y_test, prediction) 사용 선형 확인
- sns 사용 정규분포 확인

https://www.kaggle.com/faressayah/linear-regression-house-price-prediction#1.-Linear-Regression


----------
##Behavioral Cohort Studies##

Gender & Generation Cohort

Results
This research provides evidence that members of different generational cohorts possess different attitudes about hygiene, location and entertainment attributes of a shopping mall.

https://www.researchgate.net/profile/Vanessa-Jackson-6/publication/232407862_Mall_attributes_and_shopping_value_Differences_by_gender_and_generational_cohort/links/5a215e3aa6fdcc6a18bdd851/Mall-attributes-and-shopping-value-Differences-by-gender-and-generational-cohort.pdf
