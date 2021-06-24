
# 알고리즘 #

**참고 자료

https://eda-ai-lab.tistory.com/522


http://docs.likejazz.com/cosine-sim/
(코사인 유사도)



구매 패턴 유사 고객 선호 상품, 유사 상품 관련

## 1. 협업 필터링(Collaborative Filtering) ##

**설명
많은 사용자들로부터 얻은 기호 정보에 따라 사용자들의 관심사들을 자동적으로 예측하게 해주는 방법
ex) 이 상품을 구매한 사용자가 구매한 다른 상품들

1) 사용자 기반 추천(User-based Recommendation)
나와 비슷한 성향을 지닌 사용자 기반으로 그 사람이 구매한 상품을 추천

2) 아이템 기반 추천(Item-based Recommendation)
내가 이전에 구매했던 아이템을 기반으로 그 상품과 유사한 다른 상품을 추천
상품 간 유사도: 함께 구매되는 경우의 빈도 분석

==> 한계: 콜드 스타트(Cold Start) '기존 데이터'가 필수 요소, 긴 시간 소요, 
롱테일(Long Tail) 소수의 콘텐츠가 전체 추천 콘텐츠로 보이는 비율이 높아짐 '비대칭적 쏠림 현상'

https://brunch.co.kr/@biginsight/15

**코드 예시

1) 넷플릭스 영화 추천(아이템 기반 필터링)
https://diane-space.tistory.com/90

2) movie rating(사용자 기반 필터링)
https://inuplace.tistory.com/596

3) TV 애니매이션 프로그램
https://alex-blog.tistory.com/entry/Collaborative-Filtering?category=910276



## 2. 컨텐츠 기반 필터링(Contents-based Filtering)

**설명 및 코드
콘텐츠 자체에 대한 분석을 기반으로 추천\
상품 상세 페이지 상품 설명 분석(텍스트 정보가 많아야 함)\
==> 기계 / 사람이 분류\
ex) 넷플릭스 : 50명의 태거(Tagger)에 의해 분류, 사람이 단 태그를 바탕으로 콘텐츠를 5만 종으로 나눠 정리

https://techblog-history-younghunjo1.tistory.com/115


## 3. 연관 규칙 분석
항목들 간의 관계를 If-Then 형식으로 찾아 나가는 분석 방법\
= 장바구니 분석 (Market Basket Analysis)\
대용량 DB에서 기존에 발견할 수 없었던 항목 간 흥미로운 관계 탐색 가능


Association Rule의 3가지 척도
1. Support - 전체 경우의 수에서 두 아이템이 같이 나오는 비율
2. Confidence - X가 나온 경우 중 X와 Y가 함께 나올 비율
3. Lift - X와 Y가 같이 나오는 비율 / X가 나올 비율 * Y가 나올 비율

**설명)
https://hezzong.tistory.com/entry/python-%EC%97%B0%EA%B4%80%EA%B7%9C%EC%B9%99%EB%B6%84%EC%84%9DA-Priori-Algorithm \
원리) https://rfriend.tistory.com/192 \
https://zephyrus1111.tistory.com/119

**Apriori Algorithm 간략 예시)
https://sejun-s.tistory.com/15?category=830612


## 4. 순차 패턴 분석

**설명)
순서 의미를 갖는 데이터(Time Stamp)\
Support 척도만 제공

https://blog.linewalks.com/archives/6467
http://dmqm.korea.ac.kr/uploads/seminar/DMQA-Seminar-SPM.pdf
