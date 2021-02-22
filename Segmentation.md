
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
 - Ref. : https://yganalyst.github.io/ml/ML_clustering/#%EA%B5%B0%EC%A7%91%EB%B6%84%EC%84%9D%EC%9D%98-%EC%9C%A0%ED%98%95 
 
**RFM Code example** 
Ref.: https://zephyrus1111.tistory.com/16

 ----------

**방법5) Cohort analysis**
‘특정 기간 특정 경험을 공유한 집단 간 행동패턴을 비교 및 분석’ . 분류된 그룹은 상호 베타적(mutually exclusive)

 - Ref. : https://blogs.adobe.com/digitaldialogue/data-driven-marketing-ko/cohort-analysis-for-effective-remarketing-kr/
 
**Cohort Code example** 
Ref.:https://www.kaggle.com/hokyun/basic-customer-segmentation-korean-ver / https://workingwithpython.com/pythoncohortanalysis/
