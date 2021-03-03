## Starbucks offers: Advanced customer segmentation with Python ##

**marketing offers에 대한 반응과 행동을 기준으로 segmentation**

 1. Customer Profiles
나이/성별/소득/회원가입일
 2. Portfolio
30일 간/ web, email, mobile, social media channels
Offers Categories: Discount/ Buy-one-get-one(BOGO), Informational
 3. Transcript
receive/view/complete
view rate=>conversion rate

**전처리 작업**
null값 처리(평균값 대체...)
data scale 을 맞추기 위해 One-hot-encoding
outlier 제거(나이...)
중복 카운트는 첫번째 응답만 반영
...

306,534 이벤트(==>10개 타입으로 분류)
17,000 명(==>클렌징 후 14,808 명)

 - 평균 나이 53세
 - 남자가 majority(전체 평균 나이보다 younger)
 - 평균 소득 $61,800
 - 여자가 소득 higher(평균 나이도 higher)


**algorithms**
PCA & k-means

 - StandardScaler 사용해서 scaling
 - k-means: dimensions의 수가 적을때 유용
차원을 축소하기 위해 PCA(Principal Component Analysis)-주성분 분석 사용!
PCA: 가장 간단, 흔히 사용하는 차원 축소 알고리즘. 특성들이 통계적으로 상관관계가 없도록 데이터셋을 회전시키는 기술
 - cluster 갯수 찾기 : elbow method and silhouette score heuristics

밀도기반 clustering algorithms

 - DBSCAN
elbow method 사용해서 eps 찾아냄
 - OPTICS

=> k-means가 더 뚜렷한 결과
왜? DBSCAN과 OPTICS는 성별, 멤버십 기간 등 밀도 기반의 변수들만 강조하는 경향
k-means는 conversion rates를 기준으로도 clustering 가능

4개의 segment로 나뉨
1. received BOGO offers
2. BOGOs and discounts 전환 높음. 빈번한 구매
3. receive no BOGO offers. offers없이도 평균적인 구매는 이루어질 것
4. receive regular offers but never convert/ male, low income (==>마케팅에서 제외할 segment)

**conclusion**
1. cleaning and feature engineering : 80%
2. many challenges(same offer over different channels, imperfect conversion attribution...)
==> generate more accurate data on the source of each conversion, using coupon codes... through app
3. missing values imputing issue(supervised ML algorithm)


----------


## Behavioral cohorts: identify users with similar behaviors ##

Behavioral cohorts: user actions taken within a specific time period
1. Click New => Cohort
2. Click any of the conditions(**performed event,** had been active, had been new, had property, had propensity)
3. dropdown and select the event you are interested in
count events: four options 
count: 이벤트 발생 횟수(최근 30일 동안 favorite song or video를 다섯 번 이상 실행한 모든 사용자)
relative count: 두 이벤트 빈도를 비교 (30일 동안 Play Song or Video보다 favorite song or video를 더 큰 빈도로 실행한 사용자)
total sum of property: 특정 이벤트나 사용자 속성 합계를 사용해 이벤트 실행한 사용자(최근 30일 동안 총 지속 시간 값이 60초 이상 play or search song을 실행한 모든 사용자)
distinct values of property: 분석 중인 특정 값 또는 값 집합까지 이벤트나 사용자 속성을 필터링(둘 이상의 장치에서 favorite song or video 사용자)
4. set the operator(equal to, greater than, less than, etc) and the value (i.e., the count value) of this parameter.
5. 이벤트가 일어나는 기간 설정(During/Since/Within)
6. 이벤트나 추가 조건 설정 가능(And also/ And not who)

Microscope 기능을 이용해 특정 고객들의 Cohort를 별도로 생성 후 분석 가능
reference: https://blog.ab180.co/posts/amplitude-retention

Composition with cross property values
Retention if you have multiple returning events
Usage interval view in retention
Funnels with exclusion events
Funnels with constant property group-bys
Distribution views in funnels (Time to Convert + Frequency)
Event segmentation for properties (PropSum + PropAvg)
Any chart depending on a different cohort


----------


## Behavioral cohorts: identify users with similar behaviors ##

Behavioral cohorts: user actions taken within a specific time period
1. Click New => Cohort
2. Click any of the conditions(**performed event,** had been active, had been new, had property, had propensity)
3. dropdown and select the event you are interested in
count events: four options 
count: 이벤트 발생 횟수(최근 30일 동안 favorite song or video를 다섯 번 이상 실행한 모든 사용자)
relative count: 두 이벤트 빈도를 비교 (30일 동안 Play Song or Video보다 favorite song or video를 더 큰 빈도로 실행한 사용자)
total sum of property: 특정 이벤트나 사용자 속성 합계를 사용해 이벤트 실행한 사용자(최근 30일 동안 총 지속 시간 값이 60초 이상 play or search song을 실행한 모든 사용자)
distinct values of property: 분석 중인 특정 값 또는 값 집합까지 이벤트나 사용자 속성을 필터링(둘 이상의 장치에서 favorite song or video 사용자)
4. set the operator(equal to, greater than, less than, etc) and the value (i.e., the count value) of this parameter.
5. 이벤트가 일어나는 기간 설정(During/Since/Within)
6. 이벤트나 추가 조건 설정 가능(And also/ And not who)

Microscope 기능을 이용해 특정 고객들의 Cohort를 별도로 생성 후 분석 가능
reference: https://blog.ab180.co/posts/amplitude-retention

Composition with cross property values
Retention if you have multiple returning events
Usage interval view in retention
Funnels with exclusion events
Funnels with constant property group-bys
Distribution views in funnels (Time to Convert + Frequency)
Event segmentation for properties (PropSum + PropAvg)
Any chart depending on a different cohort



----------


## Customer-segmentation-and-consumer-behavior-analysis ##

Topic1

 - 구매 행동을 기준으로 소비자 세그먼트
k-means clustering algorithm 사용
Elbow method 이용 optimal number of segments: 3
 - k-means 결과 3개의 segments로 분류
1. channel과 region을 dummy로 만들어서 segment별 분류
==> majority of customers are from Channel 2 / Region 3
2. Product별 분류
==> product별로 주요 segment가 다름



Topic2

80/20 rule (Pareto principle)- 파레토법칙

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
