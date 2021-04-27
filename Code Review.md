코드 예시

1. 신용카드 거래 데이터 시각화(요일별 월별 세분화)

https://dacon.io/competitions/official/42473/codeshare/427?page=1&dtype=recent 


----------
2. Prophet Forecasting Library

https://dining-developer.tistory.com/25 

----------
3.  제주 신용카드

https://dacon.io/competitions/official/235615/codeshare/1228?page=2&dtype=recent 

==> features: 이용고객수(명), 이용건수(건), 이용금액(원)\
target: 이용금액(원)

==> 연/월별 업종,카드사용지역,거주지역,연령,성별,생애주기에 따른 차이를 그래프로 확인

----------
4. 포스트 코로나 소비패턴

https://dacon.io/competitions/official/235618/codeshare/1524?page=1&dtype=recent 

----------
5.  ~~신용카드 매출 예측~~ (4/16 리뷰)

https://dacon.io/competitions/official/140472/codeshare/1734?page=1&dtype=recent 
https://dacon.io/competitions/official/140472/codeshare/953?page=1&dtype=recent 

==> 카드 거래 데이터 이용, 각 상점별 3개월 총 매출 예측

월별로 데이터 묶어서 상점 매출을 시계열로 확인\

결측치 채우기(방법 : 보간법(Quadratic interpolation)/ 최근접 이웃 평균(Mean of nearest neighbors)/ Mean of seasonal counterparts)\

시계열 모델이므로 연도, 월 변수, 매출액 변수 유지\
각 상점별 매출 특성과 분포가 다르므로 개별적인 시계열 모델링\

ARIMA 모델 사용\
단순 correlation가 선형관계가 있다면 추세(cointegration)관계까지 고려.

----------
6. ~~아파트 실거래가 예측~~

https://dacon.io/competitions/official/21265/codeshare/439?page=1&dtype=recent 

----------
7. ~~House Price Prediction~~

https://www.kaggle.com/faressayah/linear-regression-house-price-prediction 

데이터 셋\
같은 지역의 거주자 평균 소득\
같은 지역의 평균 주택 년수\
같은 지역 주택의 평균 방 개수\
같은 지역 주택의 평균 화장실 개수\
주택 지역의 인구 수\
주택 가격\
주택 주소\
Linear Regression Model ⇒ y: Price\
RANSAC Regression \
https://gnaseel.tistory.com/33 

----------
8. 전력수요량

https://dacon.io/competitions/official/196878/codeshare/416?page=1&dtype=recent 

weather_hour (온도)데이터 없음\
일시와 기온 사용\
전주에 사용한 전력량의 표준편차, 평균 사용\
시간 컬럼 ⇒ month, week, weekday, day, hour 각각 생성, 주말/휴일 여부, 다음날\
target 변수 이상치 제거 3sigma\
시간이 i인 행의 target 값이 시간이 i인 행에서 그 시간 보다 작으면 0으로 채우고, 크면 그대로 한 것의 평균값에 표준편차의 3배를 곱한다..?






----------

**시계열 데이터 분석**
정리

https://post.naver.com/viewer/postView.nhn?volumeNo=28094462&memberNo=18071586 

https://m.blog.naver.com/bluefish850/220749045909 
