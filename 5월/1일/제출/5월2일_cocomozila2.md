/* 1번 */
SELECT b.dname, a.ename, (a.sal * 12) AS '연간 총 급여 '
  FROM scott.emp a, scott.dept b
 WHERE a.deptno = b.deptno
   AND b.dname = 'sales';
   
/* 2번 */
SELECT ename
  FROM scott.emp
 WHERE ename LIKE '%s%';
 
/* 3번 */
SELECT ename, RANK() OVER(ORDER BY sal DESC), sal
  FROM scott.emp
 WHERE ename LIKE '%n';
 
/* 4번 */
SELECT SUM((CHAR_LENGTH(ename)-CHAR_LENGTH(REPLACE(ename,'A',''))+1)) AS sumAlphaBet
  FROM scott.emp;
  
/* 5번 */
SELECT RANK() OVER(ORDER BY AVG(sal) DESC) AS 'rank', job, AVG(sal)
  FROM scott.emp
       GROUP BY job;