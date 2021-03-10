## Customer-segmentation-and-consumer-behavior-analysis ##

80/20 rule (Pareto principle)- 파레토법칙

Topic1

 - 구매 행동을 기준으로 소비자 세그먼트
k-means clustering algorithm 사용
Elbow method 이용 optimal number of segments: 3
 - k-means 결과 3개의 segments로 분류
1. channel과 region을 dummy로 만들어서 segment별 분류
==> majority of customers are from Channel 2 / Region 3
**dummy로 만드는 이유 생각해보기**

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
하지만, 1, 2, 3 같이 변경하고 예측하면 잘못된 관계를 형성할 수 있음(1+2=3)
⇒ 고유 값의 개수만큼 컬럼 만들어 예측

2. Product별 분류
==> product별로 주요 segment가 다름


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


----------
##가상 쇼핑몰 고객 주문 데이터##
data set
온라인 리테일 사이트의 2010/12-2011/12간의 주문 기록 데이터
약 500,000건의 데이터
출처: UCI ML Repository

매출, 가장 많이 팔린 아이템 확인/ 월별 top3 아이템 판매량 추이
시간별, 지역별 가장 많이 팔린 아이템 확인
우수 고객 선별(가장 소비를 많이 한 고객)- 고객 코호트 분석
 -  구매 횟수 기준
 retail.groupby('CustomerID').count()['Quantity'].sort_values(ascending=False)
 -  지불 금액 기준
 retail.groupby('CustomerID').count()['CheckoutPrice'].sort_values(ascending=False)

월간 사용자 cohort를 바탕으로 월별 재구매율(retention) 분석하기
heatmap 사용 

첫구매 월 / 재구매 월
기준이 되는 월과 그 월로부터 지난 기간의 고객 수를 계산


----------
##Unsupervised Learning- A Road to Customer Segmentation##

The first step towards the road to individual personal customization is group-of-many or as we call it fondly- Segmentation.

 - 2 very basic characteristics of a good segment
1. the segments in which the customers belong to should not change too much with time.
2.  to ensure that the segment is designed based on the use case.

RFM segmentation 
Example) 2 customers both of whom have spent $1000 in the last one month on a mobile phone e-commerce platform
1. the young technologist who purchased Apple i-Phone and is likely to purchase a phone whenever a new Apple product is launched
2. the other person who made a purchase because his/her last phone was outdated after years of use.
⇒ same category
