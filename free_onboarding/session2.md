- 트랜잭션 - 면접질문!
  1. 작업의 완전성을 보장한다
  2. 사용자의 작업셋을 모드 완벽하게 처리하거나
  3. 처리하지 못하면 원상태로 복구
- MySQL 스토리지 엔진
  - 데이터 읽고 쓰기 담당
  - `InnoDB`가 디폴트
    - 버퍼링
    - 외래키
    - 트랜잭션



- Database Lock

  1. 단어 그대로 '잠금'
  2. 하나의 데이터를 동시에 여러명이 조작할 수 없도록
  3. 동시성을 보장
  4. MySQL엔진락 vs InnoDB 락

- 락 종류

  - 글로벌 락

    - 서버 전체에 락
    - select 가능 나머지 안됨

  - 테이블 락

    - 특정 테이블에 대한 lock
    - `LOCK TABLES innodb READ`
    - `UNLOCK TABLES`

  - 네임드 락

    - 임의로 이름을 걸어줌
    - `SELECT GET_LOCK(이름, 시간)`

  - 메타데이터 락

    - DB 객체의 이름이나 구조를 변경하는 경우에 획득
    - 별도의 명령어 X, 자동으로 release

  - --------------

  - 레코드 락

    - record / row에 lcok을 거는것

  - Auto Increment Lock

  - 데드락



- 격리수준
  - 여러 트랜잭션이 동시에 처리될 때 특정 트랜잭션이 다른 트랜잭션에서 변경하거나 조회하는 데이터를 볼 수 있게 허용할지 말지 결정함
  - read uncommitted == dirty read
    - 트랜잭션 변경 내용이 commit이나 rollback 여부 상관 없이 보임
    - 에러가 발생해서 rollback된 항목을 commit 전에 접근해서 에러가 발생할 수 있음
  - read committed
    - 트랜잭션이 완료된 데이터만 다른 트랜잭션에서 조회 가능
  - unrepeatable read
    - 트랜잭션 id가 들어감
    - 커밋한게 다 보임
  - repeatable read
    - 하나의 트랜잭션에는 하나의 결과
    - phantom read
      - 언두 레코드에는 lock을 걸 수 없어서 같은 트랜잭션에서 조회 가능
      - 왔다갔다 해서 phantom read(유령)이라고 함
  - SERIALIZABLE
    - 하나의 트랜잭션에서 락을 가지고 있는 레코드에 다른 트랜잭션이 접근할 수 없음
    - 무조긴 LOCK을 획득해야함
    - InnoDB에서는 필요 없음