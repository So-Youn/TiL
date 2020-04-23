1번.

SQL> select concat(ename,concat('의 급여',concat(sal,'만원')))
 2  from emp
 3  where sal < 1000;



2번.

SQL> select ename,hiredate
 2  from emp
 3  where substr(hiredate,1,2)=81;

3번

SQL> select ename,job,lpad(sal,4,'*')
 2  from emp
 3  where sal<=2000;

4번.

SQL> select ename,job,ltrim(lpad(sal,4,'*'),'*')
 2  from emp
 3  where sal<=2000;

5번

select empno,ename,lower(job),deptno
from emp;

6번.

SQL> select empno, ename, job, sal,deptno
  2  from emp
  3  where substr(ename,1,1)>'K' and
  4  substr(ename,1,1)<'Y'
  5  order by ename;



7번

SQL> select deptno,ename,ltrim(job,'A') 담당업무,ltrim(sal,1)급여
  2  from emp
  3  where deptno=10;





0.

SQL> select ename, mgr,nvl2(to_char(mgr),'담당', '상위자') 관리자
 2  from emp;

문제 1



SQL> select  nvl(to_char(department_id),'no department') 부서번호,round(avg(salary),0) 평균급여
 2  from employees
 3   group by department_id
 4   having avg(salary)>6000;

문제2


SQL> select department_id ,avg(salary)
 2  from employees
 3  group by department_id
 4  having avg(salary)>=10000;

문제3

SQL> select department_id, avg(salary)
 2  from employees
 3  where department_id not in (40,50)
 4  group by department_id
 5  order by avg(salary) desc;

문제 4

SQL> select first_name, last_name,salary,commission_pct,round(salary+commission_pct,0) total
 2  from employees
 3  where commission_pct is not null
 4  group by first_name,last_name,salary,commission_pct
 5  order by total desc;