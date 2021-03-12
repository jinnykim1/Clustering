## Unsupervised Learning- A Road to Customer Segmentation##

The first step towards the road to individual personal customization is group-of-many or as we call it fondly- Segmentation.

 - 2 very basic characteristics of a good segment
1. the segments in which the customers belong to should not change too much with time.(세그먼트가 자주 바뀌면 안됨)
2.  to ensure that the segment is designed based on the use case.(이전에 사용했던 사례를 바탕으로 세그먼트 만들기)

RFM segmentation 
Example) 2 customers both of whom have spent $1000 in the last one month on a mobile phone e-commerce platform(두 명의 구매는 같은 조건)
1. the young technologist who purchased Apple i-Phone and is likely to purchase a phone whenever a new Apple product is launched(애플 마니아)
2. the other person who made a purchase because his/her last phone was outdated after years of use.(오래 쓴 폰..)
⇒ same category (동기나 이전의 행동패턴을 알 수 없기 때문에 같은 카테고리로 분류되어 같은 마케팅 대상이 될 수 있음)

Example)
1년치 영화 티켓 거래데이터(980K) 
- Transaction ID: Unique number for each line item.(각 행 고유번호⇒ 인덱스가 됨)
- Customer ID: Unique hashed number for each customer.(고객 아이디)
- Number of tickets: How many tickets were purchased by that person.(티켓 수;연속 변수)
- Ticket Type: What type of tickets were purchased for each purchased ticket(티켓 종류/ adult;adult같은 표시 dummy화 함)
- Cinema Site: Suburb for each of the cinema locations.(영화관 위치)
- Date and Time of Show(날짜, 시간)
- Name of the film(영화 제목)

OMBD api 를 통해 데이터 수집. 한 영화의 링크에 있는 숫자(movie key)로 통일
개봉 년도는 영화가 상영된 첫번째 날짜를 validation method(분석법 검증) 수행해서 도출

결과 값으로 사용자와 영화 데이터 간의 관련성을 표현할 수 있음 
(ex. 각각의 위치에서 몇 명의 고객이 어떤 영화 장르를 봤는지, 어떤 티켓 종류를 이용했는지... 등등)

17개의 지역
Assumption : 고객은 자신의 집과 가까이 위치한 영화관에서 영화를 본다.
세그멘테이션을 위한 여러 알고리즘을 시도
⇒ 같은 cluster number를 사용하여 post-hoc test를 수행하여 '위치가 다르다'는 사실이 '영화 행동'에 차이를 일으키는지의 인과 관계를 테스트

⇒ Hierarchical clustering에서 가장 좋은 결과를 얻음
cluster 개수: 3(실루엣 계수 이용)
고객 개인의 preference나 demographic profile에 따라 클러스터링 되어야 함

각 지역의 수치를 normalise 해야함. 결과의 절대적인 수치가 아니라 비율을 봐야 함(5000명 중 100명과 500명중 490명은 비율로 보면 오히려 후자가 높으니까)

demographics data에서 고객의 gender, marriage, professions, country of birth, income, professions, qualifications에 따른 profile 파악 가능
⇒ 이 profile이 행동의 차이를 만들어냈는지 Tukey test(사후검정)

Three Clusters
1. Richie Rich
- very high average income
- buy full priced tickets
- high number of graduate degree levels, managers and professionals
- most number of Gold/Luxury Class
- prefer action and sci-fi movies compare to comedy and romance movies

2.Strapped for cash
- lowest education level
- a lot more kids
-least movie watching rate
-recommended to open new cinema centers 
-service workers and labourers
-partial towards comedy, animation, adult movies

3.Sales Job Suburbs
-very high number of people in sales, administrative and clerical roles
-quite low income, unmarried people
-most of people have a Bachelors background
-discount seeker
-prefer romance, drama, musical genres
-high number of police discount tickets ⇒ many policemen

⇒ cluster에 따라 다른 business decisions를 세울 수 있음
1. 상영날짜, 하루 상영 횟수 등 지역에 따라 효율적으로 계획
2. 새로운 영화관 위치나 ROI(투자 수익율) 예측
3. 어느 지역에 어떤 장르의 영화를 마케팅 할지

고객의 home location postcodes, gender, work location etc가 주어졌다면 더 정확한 클러스터 형성 가능했을 듯

----------
## 가상 쇼핑몰 고객 주문 데이터 ##
data set
온라인 리테일 사이트의 2010/12-2011/12간의 주문 기록 데이터
약 500,000건의 데이터
출처: UCI ML Repository

변수: 주문번호/ 아이템 아이디/ 상품 설명/ 상품 주문 수량/ 주문 시각/ 상품 가격/ 고객 아이디/ 고객 거주 지역(국가)
+) Quantity * UnitPrice; 고객의 총 지출 비용(CheckoutPrice)


분석 목표

**1.매출, 가장 많이 팔린 아이템 확인**

 - 시간별, 지역별 가장 많이 팔린 아이템

월별 총매출(11월이 가장 높지만 12월의 전체 데이터 반영X), 

요일별 총매출(토요일 데이터 없음, 목요일까지 증가세 이후 하락), 

시간별 매출(12시까지 증가세, 3시 이후 급락)

(현상파악==>가설 생성==>확인)

- 제품별 metrics 

Top10 판매 제품(Quantity), Top10 매출 제품(CheckoutPrice)


 - 월별 top3 아이템 판매량 추이(Quantity,CheckoutPrice)


**2.우수 고객 선별(가장 소비를 많이 한 고객)- 고객 코호트 분석**

목표

1. 우수 고객 확인

- 구매 횟수 기준 CustomerID, Quantity

 -  지불 금액 기준 CustomerID, CheckoutPrice


2. 월간 사용자 cohort를 바탕으로 월별 재구매율(retention) 분석하기

- heatmap 사용
1.첫 주부터 일주일이 지날 때마다 재구매율이 얼마나 줄어드는지 확인
사용자 기준으로 최초 구매한 월 계산(retail['MonthStarted'] = month_group.transform(np.min))
2.기준이 되는 월과 실제 구매 월의 차이 계산
(retail['MonthPassed'] = (retail['Month'].dt.year - retail['MonthStarted'].dt.year) * 12 + (retail['Month'].dt.month - retail['MonthStarted'].dt.month)
3.기준 월과 MonthPassed를 기준으로 고객 카운팅
(각 기준 월에서 몇 달이 지났는지에 따라 구간을 나누고 각 구간별 고객의 수)
4.pivot 함수 이용 테이블 변경
5.heatmap으로 시각화
