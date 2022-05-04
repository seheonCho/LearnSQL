1
SELECT *
  FROM scott.emp;

2
SELECT empno, ename, sal
  FROM scott.emp
       ORDER BY ename DESC;

3 
SELECT a.sal, a.ename, a.empno, b.loc
  FROM emp a, dept b
 WHERE a.deptno = b.deptno
	   ORDER BY a.deptno ASC;

4
SELECT ename, (sal*12)
  FROM scott.emp
       ORDER BY hiredate DESC;
       
5
SELECT DISTINCT job
  FROM scott.emp;
  
7
SELECT ename, mgr
  FROM scott.emp
 WHERE empno > 7521;
 
8
SELECT sum(sal)
  FROM scott.emp
 WHERE job = 'clerk';
 
9
SELECT b.grade, a.empno 
  FROM emp a, salgrade b
 WHERE a.sal
	   BETWEEN b.losal
                   AND b.hisal
       ORDER BY a.hiredate ASC;

10
SELECT a.empno, a.ename, b.ename
  FROM emp a, emp b
 WHERE a.mgr = b.empno;
 
11
SELECT job ,sum(sal)
  FROM emp
	   GROUP BY job;
	   
	   
12
SELECT RANK() OVER(ORDER BY sum(sal) DESC) as ranking, job, sum(sal)
  FROM emp
	   GROUP BY job;