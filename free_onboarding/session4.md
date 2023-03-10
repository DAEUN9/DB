## MySQL 효율 개선하기

- index
  - PK도 인덱스
  - B-tree 구조로 관리

1. indexing
   1. 인덱스를 어디에 거는게 좋을지
      1. Cardinality
         1. 얼마나 유니크한 값들이 많은지
         2. 식당 예약을 예시로
            1. 오전 / 오후
            2. 고객 성별 남자 / 여자
      2. Update Frequency
      3. Size (인덱스 키 값의 크기)
   2. 인덱스를 충분히 활용할 수 있도록 쿼리를 작성하는 방법들에 대해 논의
      1. ORDER BY
      2. 쿼리를 잘하려면?
         1. 기본 쿼리 사용
            1. 숫자
            2. 날짜
            3. 불리언
            4. 연산자
            5. full table scan
         2. 인덱스를 잘 사용해야함.
2. normalization
   1. 데이터 중복이 어떻게 줄어드는지
   2. MySQL이 중복 데이터를 방지할 수 있기 때문
   3. 관계형 데이터베이스의 장점
3. partitioning
   1. 데이터를 나눠서 저장함
   2. 늘 좋은 것은 아님
   3. 파티션의 종류
      1. range
      2. list
      3. hash
      4. range-hash
      5. range-list
   4. partition 삭제
4. cache
   1. 자주 쓰는 건 어디다 저장했다가 가져올 수 있다
   2. 근데 8.0부터 사라짐
      1. 이론상으로는 효율에 도움이 된다고 생각했지만 실제 퍼포먼스 측면상 그렇지 않음
      2. 그리고 동시성 유지 측면에서 좋지 않음
5. 기타 query optimization