## House Price Prediction ##

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


