## 바닐라코 고객 코호트 분석
1.목적: 구매 retention 확인

2.사용데이터: 바닐라코 2020년 1월~2020년 12월 고객 주문 데이터
- 7월 데이터 누락
- 분기별 데이터 총 4개 연결

3.파이썬 사용
4.
코드 구현

https://colab.research.google.com/drive/1x5FH6lSVBSDfnfovtMesMVwFBJkWmcMd?usp=sharing


----------
**클러스터링 1-RFM**
\코드 구현

https://colab.research.google.com/drive/18VI_BFb-fdXlT_IXhogzR6npMs6qygbN#scrollTo=VhV6RI0V4Yds 

Ref.: https://www.kaggle.com/hokyun/basic-customer-segmentation-korean-ver

----------
**클러스터링 2-K-means & 클러스터링 3-Hierarchical Clustering**
코드 구현\

https://colab.research.google.com/drive/1_YBECbXrhpmtp4Q5v849kz9PGYPjjPal#scrollTo=SQJ5C4pQXg14 

Ref.: https://www.kaggle.com/hellbuoy/online-retail-k-means-hierarchical-clustering

----------
**클러스터링 4-K-means에 rfm score 대입**
코드 구현\

https://colab.research.google.com/drive/1W_ql3UBiTQYT7kfwpS4yYGn_HytmaBfv#scrollTo=fbJbbof31Lpq


----------
**앙상블 기법(ensemble method)**
더 좋은 예측 성능을 얻기 위해 다수의 학습 알고리즘을 사용하는 방법
(배깅, 랜덤포레스트, 부스팅...)

**Random Forest(의사결정나무)**
https://m.blog.naver.com/PostView.nhn?blogId=gywlsangel&logNo=221345700705&proxyReferer=https:%2F%2Fwww.google.com%2F

코드 구현\

https://colab.research.google.com/drive/1hvyOlJheX-a6m2zKfEKZGpz8Ufea9qZv#scrollTo=edV07z2Q-uL1

----------
**시계열 데이터 분석**
정리\

https://post.naver.com/viewer/postView.nhn?volumeNo=28094462&memberNo=18071586 

https://m.blog.naver.com/bluefish850/220749045909 

코드 예시\

 1. 요일별 월별 세분화
https://dacon.io/competitions/official/42473/codeshare/427?page=1&dtype=recent 

 2. Prophet Forecasting Library\
https://dining-developer.tistory.com/25 

 3.  제주 신용카드
https://dacon.io/competitions/official/235615/codeshare/1228?page=2&dtype=recent 

==> features: 이용고객수(명), 이용건수(건), 이용금액(원)\
target: 이용금액(원)\

==> 연/월별 업종,카드사용지역,거주지역,연령,성별,생애주기에 따른 차이를 그래프로 확인

4. 포스트 코로나 소비패턴
https://dacon.io/competitions/official/235618/codeshare/1524?page=1&dtype=recent 

 5.  ~~신용카드 매출 예측~~ (4/16 리뷰)
https://dacon.io/competitions/official/140472/codeshare/1734?page=1&dtype=recent 
https://dacon.io/competitions/official/140472/codeshare/953?page=1&dtype=recent 

==> 카드 거래 데이터 이용, 각 상점별 3개월 총 매출 예측\

월별로 데이터 묶어서 상점 매출을 시계열로 확인\

결측치 채우기(방법 : 보간법(Quadratic interpolation)/ 최근접 이웃 평균(Mean of nearest neighbors)/ Mean of seasonal counterparts)\

시계열 모델이므로 연도, 월 변수, 매출액 변수 유지\
각 상점별 매출 특성과 분포가 다르므로 개별적인 시계열 모델링\

ARIMA 모델 사용\
단순 correlation가 선형관계가 있다면 추세(cointegration)관계까지 고려.

 6.~~2020 D CUP Google Analytics 데이터~~(4/16 리뷰)
https://dacon.io/competitions/official/235683/codeshare/2341?page=1&dtype=recent 

시간별로 된 데이터를 일별로 수정. \
모든 값이 결측치인 행 제거\

사용자: login data, 신규 방문자 수: user가입수,  세션, 페이지뷰\
+)
날짜별 제출 횟수, 제출이 발생한 대회수, 제출한 팀 수, 제출한 유저수, 요일, 주말 여부 등 파생변수 생성 ==> 상관관계 보기\

여러 모델 중 LR이 성능이 가장 좋아서 LR사용\

[바닐라코 데이터 적용]\
Promotion = Competition\
Promotion product = Competition result\

필요 변수: \
train 데이터\
date, 사용자 수, 세션 수, 신규방문자 수, 페이지뷰 수 \

promotion 데이터\
프로모션 시작, 종료 일자 (날짜별 프로모션 시작/종료 수),\
프로모션명, 제품명 (파생: 날짜별 프로모션과 제품이 구입된 횟수)\
==>프로모션 별로 제품이 하나인지 여러개인지 확인\

user 데이터\
date, user id (날짜별 가입 유저 수)\

login 데이터\
date, user id, login id(==>?), platform, browser\
날짜별 로그인 수\
날짜별 접속한 유저 수\
날짜별 사용한 플랫폼 수\
날짜별 사용한 브라우저 수\

submission 데이터 \
date, user id, 프로모션명, 제품명\
날짜별 총 제품 구입 횟수, 날짜별 구매가 일어난 프로모션 제품 수, 구입한 고객 수\

파생: 요일, 주말 여부\

정리: date, 사용자 수, 세션 수, 신규방문자 수, 페이지뷰 수 \
프로모션 시작/종료 일자, 프로모션명, 구매제품명\
date, user id\
date, user id(방문시 부여되는 id), login id(로그인 한 id), ~~platform, browser~~\
date, user id, 프로모션명, 제품명\


7. ~~아파트 실거래가 예측~~
https://dacon.io/competitions/official/21265/codeshare/439?page=1&dtype=recent 

8. ~~House Price Prediction~~
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

9. 전력수요량

https://dacon.io/competitions/official/196878/codeshare/416?page=1&dtype=recent 

weather_hour (온도)데이터 없음\
일시와 기온 사용\
전주에 사용한 전력량의 표준편차, 평균 사용\
시간 컬럼 ⇒ month, week, weekday, day, hour 각각 생성, 주말/휴일 여부, 다음날\
target 변수 이상치 제거 3sigma\
시간이 i인 행의 target 값이 시간이 i인 행에서 그 시간 보다 작으면 0으로 채우고, 크면 그대로 한 것의 평균값에 표준편차의 3배를 곱한다..?
