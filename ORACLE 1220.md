## 1. JOIN( 결합 )

> JOIN은 정규화된 테이블이나 혹은 일반적으로 작성된 여러 테이블의 컬럼을 이용해서 데이터를 조회하는 것.

- 조인은 관계형 데이터 베이스에서 반드시 알아야하는 개념이다.

- 기본키와 외래키의 관계를 이용해서 테이블을 조인한다.

  - 외래키를 가지고 기본키 테이블에서 값을 비교하여 작업이 진행된다.

  - 조인을 하는 경우 무조건 where절에 조인조건을 정의해야한다.
  - 테이블을 여러개 사용하는 경우 모든 테이블의 조인조건을 정의해야 하며, select 절에서 사용하지 않고 조건으로만 사용한다고 하더라도 조인조건은 정의해야한다.

- (PK, FK관계)두 테이블의 연관성 있는 컬럼을 통해 내가 원하는 데이터(하나의 결과)를 가져다 쓰는 것.

### [ 조인방법]

1. from 절에 조회하고 싶은 데이터가 저장된 테이블을 모두 명시한다.

2. 조인을 하는 경우 컬럼이 어떤 테이블의 컬럼인지 명확하게 정의하기 위해 **테이블명.컬럼명**으로 액세스 한다.

3. from절에 테이블명을 정의하면서 alias를 함께 추가하여 alias를 통해 액세스하도록 한다.

   ``` sql
   select alias.컬럼명, alias.컬럼명...
   from 테이블1 alias1, 테이블2 alias2
   ```

4. where절에는 반드시 조인조건을 추가하며 조인조건에는 두 테이블의 값을 비교하기 위해 정의하는 것이므로 외래키와 기본키를 정의한다. 

   - 외래키 테이블(Child 테이블)에 정의된 컬럼값을 기본키 테이블(Parent 테이블)에서 비교하여 정확하게 일치하는 경우 값을 가져온다.
     - 테이블 2개 -> 조인조건 1개
     - 테이블 3개 -> 조인조건  2개

``` sql
SQL> select d.dname, e.ename,e.sal
  2  from emp e, dept d
  3  where e.deptno = d.deptno -- 비교해서 일치하는 것의 네임 표기
  			and sal>=300;
```

[예제]

**부서별 인원수 구하기(단, 부서명으로 출력하기)**

``` sql
SQL> select d.dname,count(e.empno)
  2  from emp e, dept d
  3  where e. deptno = d. deptno
  4  group by d.dname;
```
**DALLAS에근무하는사원중급여1500 이상인사원의이름,급여,업무, 입사일, 보너스를조회**

``` sql
SQL> select e.ename, e.sal,d.dname,e.hiredate,e.comm
  2  from emp e, dept d, locations l
  3  where e. deptno = d. deptno and d.loc_code = l.loc_code and e.sal>=1500 and 						l.city='DALLAS';
```

- emp 와 dept 테이블 두개만 쓴다고 하더라도, where 절의 사용을 위해 locations을 조인조건에 언급해줘야 한다.