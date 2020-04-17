## LIKE

정확한 키워드를 모를 경우 와일드카드(__%__ _____ )를 사용하여 일부만으로 검색하는 방법

% : S% (S로 시작하는 것), %S( S로 끝나는 것), %S%(S가 중간에 있는 것)

_ : 자리 수

* LIKE 자체가 DBMS에 부담이 가기 때문에 Like에 OR와 같은 논리연산자는 중복하지 않는 것이 좋다

잘못된 예)

``` sql
select * from "테이블 명" where like "컬럼 명" or like "컬럼 명"
```

ex)  __%__ 사용 예

``` sql
select * from emp where ename like 'S%';
select * from emp where ename like '%S';
select * from emp where ename like '%S%';
```

ex) _____ 사용 예

``` sql
select * from emp where ename like 'A____'
```



## NULL

NULL이란 해당 컬럼 값이 없다는 의미

NULL값을 가지고 있는 컬럼을 검색하려면 is NULL을 사용

NULL이 아닌 것을 검색하려면 is not NULL 사용

ex)

``` sql
select * from emp where mgr is null;
select * from emp where comm is not null;
```

 

#### NULL 함수 

숫자 컬럼을 연산해야 할 때 NULL을 처리해 주는 함수

##### NVL(a,b)

1번째 값이 null 이 아니면 1번째 값, null이면 2번째 값을 넣어라

##### NVL2(a,b,c)

1번째 값이 null 이 아니면 2번째 값, null이면 3번째 값을 넣어라

##### COALESCE(a,b,c)

1번째 값이 null 이 아니면 2번째 값 null이면 3번째 값

- SUM(), AVR() 같은 숫자연산/집합함수는 NULL처리가 이미 포함되어 있음

``` sql
select ename, nvl(comm*1.5,0) from emp;
select ename, nvl2(comm*1.5, 'Y', 'N') from emp;
```



## GROUP BY

집합 함수와 같이 사용해 그룹별 연산을 적용한다.

ex) emp 테이블의 부서별 직원수를 구하시오

``` sql
select dept.dname, count(dept.dname) as number_count from emp join dept on emp.depno = dept.deptno group by dept.dname;
```

 

### HAVING

Group By 절에서 Where 대신 사용

ex)

``` sql
select dept.dname, count(dept.dname) as number_count from emp join dept on emp.depno = dept.deptno group by dept.dname gaving count(dept.dname) >= 5;
```

