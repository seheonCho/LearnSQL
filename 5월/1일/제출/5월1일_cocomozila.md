SELECT *
  FROM scott.emp;
  
SELECT empno, ename, sal
  FROM scott.emp
       ORDER BY ename DESC;
       
SELECT a.sal, a.ename, a.empno, b.loc
  FROM emp a, dept b
 WHERE a.deptno = b.deptno
	   ORDER BY a.deptno ASC;
       
SELECT ename, (sal*12)
  FROM scott.emp
       ORDER BY hiredate DESC;

SELECT job
  FROM scott.emp
	   group by job;
       
SELECT DISTINCT job
  FROM scott.emp;
       
SELECT ename, mgr
  FROM scott.emp
 WHERE empno > 7521;
 
SELECT sum(sal)
  FROM scott.emp
 WHERE job = 'clerk';
 
SELECT b.grade, a.empno 
  FROM emp a, salgrade b
 WHERE a.sal
	   BETWEEN b.losal
                   AND b.hisal
       ORDER BY a.hiredate ASC;
       
SELECT a.empno, a.ename, b.ename
  FROM emp a, emp b
 WHERE a.mgr = b.empno;
 
SELECT job ,sum(sal)
  FROM emp
	   GROUP BY job;
       
SELECT RANK() OVER(ORDER BY sum(sal) DESC) as ranking, job, sum(sal)
  FROM emp
	   GROUP BY job;