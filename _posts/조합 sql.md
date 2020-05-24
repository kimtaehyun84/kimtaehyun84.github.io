##	SELECT INTO

쿼리 결과를 새 테이블로 만든다.(실제로 테이블이 생김)

``` sql
create table "테이블 명" as Select * from "테이블 명"
```

ex)

``` sql
create table emp_salesman as select * from emp where job = 'SALESMAN';
```

기본적으로 View와 동일하지만 생명 주기가 다름

SQL : 비절차적 언어



## INSERT INTO SELECT

쿼리 결과를 기존의 테이블에 추가 한다.

*  SELECT 하는 테이블과 INSERT 하는 테이블은 동일한 구조를 가져야함

ex)

``` sql
insert into emp_salesman select * from emp where job = 'SALESMAN';
```



## CASE ... WHEN ... END

SQL의 조건문(If/Switch문)에 해당

``` sql
SELECT emp.ename,
	case
		when length(emp.job) > 3 then lower(substr(emp.job, 1,3))
		when length(emp.job) <=3 then lower(emp.job)
	end as abbr_job,
	emp.job
	from emp;	
		
```

