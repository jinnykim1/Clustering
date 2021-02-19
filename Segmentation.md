customer segmentation
=====================
**방법1) Non-Hierarchical Clustering(비계층적 군집분석)**

K-means: n개의 데이터와 k(<=n)개의 중심점(centroid)이 주어졌을때 각 그룹 내의 데이터와 중심점 간의 비용(거리)을 최소화하는 방향으로 계속 업데이트를 해줌으로써 그룹화를 수행하는 기법

1. 초기점(k) 설정
k는 중심점(centroid)이자, 묶일 그룹(cluster)의 수와 같다.
2. 그룹(cluster) 부여
k개의 중심점(동그라미)과 개별 데이터(네모)간의 거리를 측정한다.
가장 가까운 중심점으로 데이터를 부여한다.
3. 중심점(centroid) 업데이트
할당된 데이터들의 평균값(mean)으로 새로운 중심점(centroid)을 업데이트한다.
4. 최적화
2,3번 작업을 반복적으로 수행한다. 변화가 없으면 작업을 중단한다.
 - Ref. : https://yganalyst.github.io/ml/ML_clustering/#%EA%B5%B0%EC%A7%91%EB%B6%84%EC%84%9D%EC%9D%98-%EC%9C%A0%ED%98%95 
 
 Code example Ref.: https://www.kaggle.com/kushal1996/customer-segmentation-k-means-analysis

----------

**방법2)Hierarchical Clustering(계층적 군집분석)** 

특정 알고리즘에 의해 데이터들을 연결하여 계층적으로 클러스터를 구성해 나가는 방법(K-means와 달리 클러스터의 개수를 미리 가정할 필요 X)

- Ref. : http://blog.naver.com/PostView.nhn?blogId=samsjang&logNo=221019280298&parentCategoryNo=&categoryNo=&viewDate=&isShowPopularPosts=false&from=postView

Code example Ref.: https://www.kaggle.com/kratibhadada/mall-customers-clustering-analysis

----------

**방법3) RFM analysis**

고객의 과거 구매이력을 바탕으로 고객군을 분류하는 기법. RFM은 Recency, Frequency, Monetary의 약자로 고객의 가치를 다음의 세 가지 기준에 의해 계산함. 대개 직전 과거 12개월을 대상으로 함

 *Three Metrics*
 1.Recency (거래의 최근성) : 고객이 얼마나 최근에 구입했는가?
 2.Frequency (거래빈도) : 고객이 얼마나 빈번하게 우리 상품을 구입했나?
 3.Monetary Value (거래규모) : 고객이 구입했던 총 금액은 어느 정도인가?

 - Ref. : https://yganalyst.github.io/ml/ML_clustering/#%EA%B5%B0%EC%A7%91%EB%B6%84%EC%84%9D%EC%9D%98-%EC%9C%A0%ED%98%95 
 
Code example Ref.: https://zephyrus1111.tistory.com/16
