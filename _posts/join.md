# Join

## 표준조인

###	Inner Join

조인시 NULL값은 허용하지 않음

명시하지 않으면 기본적으로 INNER JOIN

ex)

```sql
select count(x) 
from employees innner join departments 
on employees.department_id = departments.department_id;
```



### LEFT JOIN

조인시 왼쪽 테이블의 NULL값을 포함해서 표시

ex)

``` sql
select count(x) 
from employees left join departments 
on employees.department_id = departments.department_id;
```



### RIGHT JOIN

조인시 오른쪽 테이블의 NULL값을 포함해서 표시

ex)

``` sql
select count(x) 
from employees right join departments 
on employees.department_id = departments.department_id;
```



###	 FULL JOIN

LEFT JOIN과. RIGHT JOIN의 합집합

ex)

``` sql
select count(x) 
from employees full join departments 
on employees.department_id = departments.department_id;
```



## ORACLE 전용 조인

### Cross JOIN

모든 경우의 수를 조합

ex)

Column(Kim, Lee)와 Column(Seoul, Busan)을 Cross Join하면

Column({Kim, Seoul}, {Kim,Busan}, {Lee, Seoul}, {Lee Busan}) 4개가 생긴다

```sql
select empno, ename, loc from emp, dep;
```



### Equi JOIN

ex) Inner Join의 또다른 형태,  on이 아닌  where를 이용하여 조인

```sql
select emp.name, dept.dname, dept.loc from emp, dept 
where emp.deptno=dept.deptno;
```



### NATURAL JOIN

따로 공통 컬럼을 명시하지 않음

natural join이라고 명시하면 자동으로 맞춰서 Inner Join을 한다.(단 공통 컬럼이 하나만 있을때 사용)

ex)

```sql
select emp.name, dept.dname, dept.loc from emp natural join dept;
```



### USING

Join의 대상이 되는 Column을 Using을 이용하여 지정한다.

ex) 

```sql
select emp.ename, dept.dname, dept.loc 
from emp join dept using(deptno)
```



### Non-equi JOIN

공통컬림이 아닌 컬럼으로 조인을 하는 것

```sql
select emp.ename, dept.dname, emp.sal 
from emp,dept 
where emp.sal between 2000 and 3000;
```



### OUTER JOIN

Left Join, Right Join과 같음

누락되지 않고자 하는 컬럼 쪽에( +를 붙임 )

ex) 

```sql
select emp.ename, dept.dname, dept.loc 
from emp, dept 
where emp.deptno(+) = dept.deptno
```



### SELF JOIN

자기 자신과 Join

ex)

``` sql
select emp2.ename, emp1.ename 
from emp emp1, emp emp2 
where emp1.empno = emp2.mgr;
```



 