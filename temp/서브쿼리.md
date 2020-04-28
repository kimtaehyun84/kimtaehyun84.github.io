## 서브 쿼리

쿼리문 내에 다른 쿼리문이 있는 형태

서브쿼리는 메인쿼리에 포함되는 관계

- ()를 사용해 감싸는 형태
- ORDER BY를 사용하지 못한다.



### 단일 행 서브쿼리(Single Row Sub Query)

- 결과가 레코드 하나인 서브 쿼리

  ex) 리서치 부서 중 연봉이 평균 이상인 사람의 이름과 연봉을 표시하시오

  ``` sql
  Select ename, sal from emp where sal > (select avg(sal)from emp where deptno = (select deptno from dept where dname = 'RESEARCH'));
  ```

  

### 다중행 서브쿼리

* 결과가 레코드 여러개인 쿼리

* 다중 행 연산자를 사용

  * ALL
    * 여러 개의 레코드의 AND 효과(가장 큰 값보다 큰)
    * Sal > ALL(Select Sal ..)
  * ANY
    * 여러 개의 레코드의 OR효과 (가장 작은 값 보다 큰)
    * Sal > ANY(Select Sal ...)
  * IN/E
    * 결과값 중에 있는 것의 의미(Sub Set의 의미)

  

  ex) 

  부서번호가 20인 부서의 모든 직원보다 연봉이 더 많은 직원의 Ename과 Sal을 표시하시오

  ``` sql 
  select ename, Sal from emp where Sal > ALL(select Sal from emp where deptno = 20);
  ```

  부서번호가 20인 부서의 어떤 직원보다 연봉이 더 많은 직원의 Ename과 Sal을 표시하시오

  ``` sql
  select ename, sal from emp where sal > any(select sal from emp where deptno = 20);
  ```

  Sal이 3000명이 넘어가는 직원명과 JOB, 부서 번호를 표시하시오.

  ``` sql
  select ename, job, deptno, from emp where (ename,job,deptno) in (select ename, job, deptno from emp where sal > 3000);
  ```

  

### 멀리 컬럼 서브쿼리

* 결과가 컬럼 여러 개인 서브쿼리

