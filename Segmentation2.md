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
