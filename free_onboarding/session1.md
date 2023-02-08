## 다양한 데이터베이스의 장/단점

- 데이터베이스의 원칙

  1. 무결성(integrity)
     - accuracy : 데이터를 처리할 때, 데이터가 변경되거나 손상되면 안됨
  2. 안정성(reliability)
     - Resilient
     - 고장이 잘 안나야함
  3. 확장성
     - Scale Up : 서버를 키우는 것
     - Scale Out : 똑같은 서버를 여러 개로 늘림

- 다양한 데이터베이스의 종류

  1. Relational(RDBMS)
     - 테이블 사용
  2. NoSQL
     - Key-Value
       - 중복 키를 사용하면 value가 덮어써짐
       - Redis
         - 확장성 떨어짐
       - DynamoDB
         - Partition Key, Sort Key 으로 나누어짐
         - 확장성 높음
     - Graph
       - Neo4j ( graph )
         - 노드간의 관계를 나타냄
     - Document
       - MongoDB
         - 구조가 자유로움, 스키마가 없어서 원하는 형식의 데이터를 넣을 수 있음
         - xml, json, html 등을 넣을 수 있음

  

  - Row Oriented Database
    - 로우 단위로 데이터 저장
    - Auto Increment를 해도 물리적으로 순서대로 저장되지 않음
    - 중간 데이터를 삭제하면 새 데이터 빈 자리에 넣음
      - 인덱스 처리를 잘 하자
    - ex) MySQL
  - Column Oriented Database
    - 컬럼 단위로 데이터 저장
    - read가 쉬움
    - ex) big query
  - CAP Theorem
    - 어떤 DB를 선택할지
    - 3개를 다 챙길 수는 없다
    - Consistency
      - 금융데이터에 중요
      - 언제나 같은 값
    - Partition-Tolerance
      - 데이터량이 엄청 많을 때
      - 분산해도 되는지
    - Availability
      - 가용성
    - Netfilix - MySQL : Consitetncy를 낮추고 Availability를 높임
    - Instagram - : Availability 중요
  - 면접 질문 - RDBMS vs NoSQL
    - RDBMS
      - 스키마 수정에 불리
      - 데이터가 보장됨
      - 스키마가 확실
      - Scale up 가능 : 분산 저장 안하고 중복이 안됨 - Scale out X
        - Scale out은 많은 양의 데이터를 흩뿌려서 저장할 수 있음
      - SQL을 통해 쉽게 데이터를 다룸
    - NoSQL
      - Scale Out에 용이함
      - 빠른 Read, write

  - Redis, MongoDB어떨 때 사용?
    - Redis: 타임아웃, 관계 등 설정
    - MongoDB: 로그
  - read와 query는 같은 맥락
  - integrity, consistency 차이
    - consistency를 integrity가 포함

