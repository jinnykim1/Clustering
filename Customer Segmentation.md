customer segmentation
=====================
**방법1) Non-Hierarchical Clustering(비계층적 군집분석)1**

K-means: n개의 데이터와 k(<=n)개의 중심점(centroid)이 주어졌을때 각 그룹 내의 데이터와 중심점 간의 비용(거리)을 최소화하는 방향으로 계속 업데이트를 해줌으로써 그룹화를 수행하는 기법

1)초기점(k) 설정
k는 중심점(centroid)이자, 묶일 그룹(cluster)의 수와 같다.
2)그룹(cluster) 부여
k개의 중심점(동그라미)과 개별 데이터(네모)간의 거리를 측정한다.
가장 가까운 중심점으로 데이터를 부여한다.
3)중심점(centroid) 업데이트
할당된 데이터들의 평균값(mean)으로 새로운 중심점(centroid)을 업데이트한다.
4)최적화
2,3번 작업을 반복적으로 수행한다. 변화가 없으면 작업을 중단한다.
 - Ref. : https://yganalyst.github.io/ml/ML_clustering/#%EA%B5%B0%EC%A7%91%EB%B6%84%EC%84%9D%EC%9D%98-%EC%9C%A0%ED%98%95 
 
 **K-means Code example** 
 Ref.: https://www.kaggle.com/kushal1996/customer-segmentation-k-means-analysis

----------

**방법2) Non-Hierarchical Clustering(비계층적 군집분석)2**

DBSCAN

밀도기반(Density-based) 클러스터링 방법으로 “유사한 데이터는 서로 근접하게 분포할 것이다”는 가정을 기반으로, K-means와 달리 처음에 그룹의 수(k)를 설정하지 않고 자동적으로 최적의 그룹 수를 찾아나감

1) 먼저 하나의 점(파란색)을 중심으로 반경(eps) 내에 최소 점이 4개(minPts=4)이상 있으면, 하나의 군집으로 판단하며 해당 점(파란색)은 Core가 된다.
2) 반경 내에 점이 3개 뿐이므로 Core가 되진 않지만 Core1의 군집에 포함된 점으로, 이는 Border가 된다.
3) 1번과 마찬가지로 Core가 된다.
4) 반경내의 점중에 Core1이 포함되어 있어 군집을 연결하여 하나의 군집으로 묶인다.

 - Ref. : https://yganalyst.github.io/ml/ML_clustering/#%EA%B5%B0%EC%A7%91%EB%B6%84%EC%84%9D%EC%9D%98-%EC%9C%A0%ED%98%95 / https://laptrinhx.com/customer-clustering-using-dbscan-3490256095/
 
 **DBSCAN Code example** 
 Ref.: https://www.kaggle.com/aeyjpn/women-love-shopping-clustering-with-dbscan

----------

**방법3)Hierarchical Clustering(계층적 군집분석)** 

특정 알고리즘에 의해 데이터들을 연결하여 계층적으로 클러스터를 구성해 나가는 방법(K-means와 달리 클러스터의 개수를 미리 가정할 필요 X)
- Ref. : http://blog.naver.com/PostView.nhn?blogId=samsjang&logNo=221019280298&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView

**Hirerarchical Clustering Code example** 
Ref.: https://www.kaggle.com/kratibhadada/mall-customers-clustering-analysis

----------

**방법4) RFM analysis**

고객의 과거 구매이력을 바탕으로 고객군을 분류하는 기법. RFM은 Recency, Frequency, Monetary의 약자로 고객의 가치를 다음의 세 가지 기준에 의해 계산함. 대개 직전 과거 12개월을 대상으로 함

 *Three Metrics*
-Recency (거래의 최근성) : 고객이 얼마나 최근에 구입했는가?
-Frequency (거래빈도) : 고객이 얼마나 빈번하게 우리 상품을 구입했나?
-Monetary Value (거래규모) : 고객이 구입했던 총 금액은 어느 정도인가?
 - Ref. : https://brunch.co.kr/@biginsight/43 / https://www.kaggle.com/hokyun/basic-customer-segmentation-korean-ver RFM 분석
 
**RFM Code example** 
Ref.: https://zephyrus1111.tistory.com/16

 ----------

**방법5) Cohort analysis**
‘특정 기간 특정 경험을 공유한 집단 간 행동패턴을 비교 및 분석’ . 분류된 그룹은 상호 베타적(mutually exclusive)
 - Ref. : https://blogs.adobe.com/digitaldialogue/data-driven-marketing-ko/cohort-analysis-for-effective-remarketing-kr/
 

**Cohort Code example** 
Ref.:https://www.kaggle.com/hokyun/basic-customer-segmentation-korean-ver / https://workingwithpython.com/pythoncohortanalysis/

----------

**방법6) Spectral Clustering**
서로 연결되어 있거나 바로 옆에 있는 대상이 같은 그룹. 두 대상의 거리가 매우 가깝더라도 대상이 연결되어 있지 않다면 같은 그룹으로 묶이지 않음.

 - Ref. : https://brunch.co.kr/@mathpresso/11
 
**Spectral Code example** 
Ref.: https://www.kaggle.com/ecedolen/machine-l-on-credit-card-customer-segmentation 
7.4 Spectral Clustering

----------

**방법7) Gaussian Mixture Model(GMM)**

개별 가우시안 모델들을 혼합하여 다양한 샘플데이터에도 강인하게 만든 모델
* 여기서 분포는 가우시안 확률 분포에 한정하지 않음
  - Ref.: https://throwexception.tistory.com/735

 - Ref. : https://brunch.co.kr/@gimmesilver/40 (확률 분포 기반 클러스터링)
 / http://bongholee.com/2020/10/%EA%B0%80%EC%9A%B0%EC%8B%9C%EC%95%88-%ED%98%BC%ED%95%A9%EB%AA%A8%EB%8D%B8gaussian-mixture-model/ 
 / https://m.blog.naver.com/PostView.nhn?blogId=sw4r&logNo=221033034225&proxyReferer=https:%2F%2Fwww.google.com%2F
 
**Gaussian Mixture Model Code example** 
Ref.: https://www.kaggle.com/ektakashyap/mall-customer-segmentation-using-gaussian-mixture


----------
**정리**


1.RFM analysis
세세한 세그먼테이션 보다는 고객에 대한 기본적인 분석을 하는데 적합한 분석법.
Who are my best customers?
Which customers are at the verge of churning?
Who has the potential to be converted in more profitable customers?
Who are lost customers that you don’t need to pay much attention to?
Which customers you must retain?
Who are your loyal customers?
Which group of customers is most likely to respond to your current campaign?
https://www.putler.com/rfm-analysis/

2.kmeans
가장 기본적인 기법. 
단점1) 가중치와 거리 정의 필요. 2) 초기 클러스터링수 결정. 3) 결과 해석의 어려움

https://lucy-the-marketer.kr/ko/growth/k-means-clustering-python-customer-data-analysis/

3.Behavioral Cohort
고객이 서비스 안에서 할 수 있는 특정 행동을 기준으로 그룹을 분류 후, 그룹의 행동패턴을 비교/분석합니다. 지표 값과 특정 행동간의 상관관계를 파악할 수 있습니다. 단, 인과관계는 설명하지 못하는 한계가 있습니다. A/B 테스트, 다변량 테스트 등을 통하여 인과관계(일 가능성이 높은 것)을 찾아낼 수 있습니다.

게시글 수 3개 이상, 친구 추가 100명 이상 등, 서비스 내 모든 액션에 대해서 가능합니다.
복수의 행동에 대해서도 그룹을 분류 할 수 있습니다.
eg. 친구가 100명 이상이면서 게시글이 3개 이상인 그룹 등
 - Behavioral Cohort more information: https://blog.amplitude.com/guide-to-behavioral-cohorting
