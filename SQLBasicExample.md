1번. 81년도에 입사한 사람들 중에서 job이 ' MANAGER'인 사람들의 성명과 직업을 다음   과 같은  형태로 출력하세요.

   ex)JONES : MANAGER

```sql
SQL> select ename ||':'|| job
 2  from emp
 3  where job = 'MANAGER'and
 4  hiredate between '1981/01/01'and'1981/12/31';
```

**where hiredate like '81%'* **

like는 문자열을 취급하기 때문에 '눈에 보이는 문자%'로 써야 한다.

ENAME||':'||JOB
\----------------------------------------
JONES:MANAGER
BLAKE:MANAGER
CLARK:MANAGER

---

2번.   job이 'SALESMAN'이면서 급여가 1500이상인 데이터를 출력 (사번,성명,직업,급여 출력)

```sql
SQL> select empno,ename,sal,hiredate
2 from emp
3 where job = 'MANAGER'and sal>=1500;
```

 EMPNO ENAME            SAL HIREDATE
------ -------------------- ---------- --------
 7566 JONES            2975 81/04/02
 7698 BLAKE            2850 81/05/01
 7782 CLARK            2450 81/06/09

---

3번.급여(sal) 2000에서 3000사이의 사원 between ~ and 연산자를 이용하여 작업. 급여가 높은 순서대로 출력하세요.(사번,성명,급여)

```sql
SQL>select empno,ename,sal
 2 from emp
 3 where sal between 2000 and 3000
 4 order by sal desc;
```

EMPNO ENAME            SAL
----- -------------------- ----------
 7902 FORD            3000
 7788 SCOTT            3000
 7566 JONES            2975
 7698 BLAKE            2850
 7782 CLARK            2450

---

4번. 82년도 이후에 입사했거나 급여가 5000이상인 사람을 출력. (사번,성명,급여,입사년월)

```sql
SQL>select empno,ename,sal,hiredate
1 from emp
2 where hiredate>='1982/01/01'
3      or sal >=5000;
```

 EMPNO ENAME            SAL HIREDATE
------ -------------------- ---------- --------
 7788 SCOTT            3000 82/12/09
 7839 KING            5000 81/11/17
 7876 ADAMS            1100 83/01/12
 7934 MILLER           1300 82/01/23

---

5번.  emp테이블에서 부서번호가 10이거나 20에 속하는 사원들 중에서 급여가 2000이상인 사원들 의 이름,급여,부서번호를 출력

```sql
SQL> select ename, sal, deptno
 2  from emp
 3  where deptno in ('10','20')
 4  and sal >=2000;
```

ENAME            SAL   DEPTNO
-------------------- ---------- ----------
JONES            2975     20
CLARK            2450     10
SCOTT            3000     20
KING            5000     10
FORD            3000     20

---

6번.  급여가 1300에서 1700사이에 해당하는 사원의 성명,담당업무,급여,부서번호 조회

```sql
SQL> select ename, job, sal,deptno
 2  from emp
 3  where sal between 1300 and 1700;
```

ENAME         JOB            SAL   DEPTNO
-------------------- ------------------ ---------- ----------
ALLEN         SALESMAN         1600     30
TURNER        SALESMAN         1500     30
MILLER        CLERK           1300     10

---

7번.  사원번호가 7902,7788,7566인 사원의 사원번호, 성명,담당업무,급여,입사일자 조회

``` sql
SQL> select empno,ename,job,sal,hiredate
 2  from emp
 3  where empno in ('7902','7788','7566');
```

   EMPNO ENAME         JOB            SAL HIREDATE
---------- -------------------- ------------------ ---------- --------
   7566 JONES         MANAGER          2975 81/04/02
   7788 SCOTT         ANALYST          3000 82/12/09
   7902 FORD         ANALYST          3000 81/12/03

---

8번. emp테이블에서 급여가 2800이상이고 job이 MANAGER인 사원의 사원번호,성명,담당업무,  급여,입사일자,부서번호를 조회하기

``` sql
SQL> select *
 2  from emp
 3  where sal >=2800
 4     and job = 'MANAGER';
```

​    EMPNO ENAME         JOB            MGR HIREDATE     SAL    COMM   DEPTNO
---------- -------------------- ------------------ ---------- -------- ---------- ---------- ----------
   7566 JONES         MANAGER          7839 81/04/02    2975           20
   7698 BLAKE         MANAGER          7839 81/05/01    2850           30

---

9번. emp테이블에서 JOB이 'MANAGER',"CLERK','ANALYST' 가 아닌 사원의 사원번호, 성명,  담당업무,급여,부서번호 출력

``` SQL
SQL> select empno, ename,job,sal,deptno
 2  from emp
 3  where job not in ('MANAGER','CLERK','AMALYST');
```

   EMPNO ENAME         JOB            SAL   DEPTNO
---------- -------------------- ------------------ ---------- ----------
   7499 ALLEN         SALESMAN         1600     30
   7521 WARD         SALESMAN         1250     30
   7654 MARTIN        SALESMAN         1250     30
   7788 SCOTT         ANALYST          3000     20
   7839 KING         PRESIDENT         5000     10
   7844 TURNER        SALESMAN         1500     30
   7902 FORD         ANALYST          3000     20

---

``` SQL
SQL> select ename, job,hiredate
  2  from emp
  3  where deptno in (10,20,30)
  4  order by job desc, hiredate desc;
```



