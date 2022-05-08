/* 1번 */
SELECT a.ename, a.hiredate, b.ename as manager_name, b.hiredate, DATE_ADD(a.hiredate, INTERVAL 1 YEAR) as '고용일로부터 1년'
  FROM emp a, emp b
 WHERE a.mgr = b.empno
       AND a.hiredate > b.hiredate;
       
/* 2번 */
SELECT CONCAT('" ',a.ename,' "의 매니저는 " ',b.ename,' "이다.') AS result 
  FROM emp a, emp b
 WHERE a.mgr = b.empno;
       
/* 3번 */
SELECT RANK() OVER(PARTITION BY job ORDER BY sal DESC) as sal_ranking, sal, empno, ename, job
  FROM emp
  ORDER BY job DESC;
  
/* 4번 */
SELECT empno, ename, hiredate
  FROM emp
 WHERE hiredate > (SELECT hiredate
                     FROM emp
					WHERE ename = 'MILLER');
 
/* 5번 */
SELECT a.* 
  FROM emp a, salgrade b
  WHERE a.sal < (SELECT AVG(a.sal)
				   FROM emp a, salgrade b
			      WHERE a.sal
						BETWEEN b.losal
						        AND b.hisal
					AND b.grade = 2);
                    
/* 6번 */
SELECT RANK() OVER(ORDER BY AVG(sal) DESC)as sal_rank, job, AVG(sal)
  FROM emp
  GROUP BY job;