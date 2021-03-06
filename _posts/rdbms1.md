
#RDBMS란?
---
데이터간 사전 정의된 관계가 있는 데이터의 모음을 말함

관계형 데이터베이스(RDB)는
>> 관계형 RDBMS 는 읽기에 최적화 된 DB
데이터의 업데이트 중심은 NoSQL (Not Only SQL)이 유용하다

RDBMS
- 관계형 데이터베이스 시스템
- 테이블 기반의 DBMS
    * 테이블/ 컬럼 형태의 데이터 저장 방식
    * 테이블과 테이블 간의 연관관계를 이용해 정보를 구하는 방식
- 모델링은 E-R(Entity Relationship) 모델을 사용
    ex) 학생, 교수 는 Entity 학생과 교수에서 유도된 수업이라는 테이블은 Relationship
    Relational -> 관계형 (전체 테이블을 뜻함)
    Relation Ship -> (Entity를 연결해서 만든 2차 테이블을 말함)
- 데이터를 테이블 단위로 관리
    하나의 테이블은 여러 개의 컬럼으로 구성
- 테이블끼리의 중복정보는 최소화
    동일한 데이터가 여러 군데 중복되어 존재하면 데이터 수정시 문제 발생 확률이 높아짐
    이를 분리 하는 것을 정규화(Normalize)라고 함
- 사용방식
    여러 테이블을 Join하여 큰 테이블을 생성 하여 사용

RDB -> 정규화를 통해 테이블을 최대한 쪼개고 Join을 하여 사용하는것이 RDB의 방식
