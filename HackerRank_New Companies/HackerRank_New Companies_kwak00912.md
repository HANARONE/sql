```sql
/* 
1단계) 이해 단계
처음에 어떤 결과를 출력해야 하는지 잘 이해가 안 됨.
그럴때 다시 생각해보면, Sample Output을 보는 게 가장 큰 도움이 되는 듯
저런 값이 출력 되려면 어떻게 해야 할지를 고민했음

2단계) 어떻게 구현할까
LEFT JOIN, GROUP BY, COUNT 함수를 활용해야 겠구나까지만 생각



*/
-- 1) 첫 번째 풀기
SELECT A.company_code, A.founder, B.CB, C.CC, D.CD, E.CE
FROM Company A  
        LEFT JOIN
    (SELECT company_code, COUNT(*) AS CB
     FROM Lead_Manager
     GROUP BY company_code) B
  ON A.company_code = B.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(*) AS CC
      FROM Senior_Manager
      GROUP BY company_code, lead_manager_code) C
  ON A.company_code = C.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(*) AS CD
      FROM Manager
      GROUP BY company_code, lead_manager_code, senior_manager_code) D
  ON A.company_code = D.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(*) AS CE
      FROM Employee
      GROUP BY company_code, lead_manager_code, senior_manager_code, manager_code) E
  ON A.company_code = E.company_code
ORDER BY A.company_code;


-- 결과를 보니 뭔가 잘못되었음
-- 반성: 할 거면 생각하고 하자 
```

```sql
Your Output (stdout) (Sample)
C1 Angela 2 5 4 15
C1 Angela 2 5 9 15
C1 Angela 2 5 4 5
C1 Angela 2 5 9 5
C1 Angela 2 5 4 14
C1 Angela 2 5 9 14
C1 Angela 2 5 4 11
C1 Angela 2 5 9 11
C1 Angela 2 5 4 8
C1 Angela 2 5 9 8
C10 Earl 1 2 3 4
C10 Earl 1 2 3 9
```

```sql
-- 2) 두 번째 풀기
SELECT A.company_code, A.founder, B.CB, C.CC, D.CD, E.CE
FROM Company A  
        LEFT JOIN
    (SELECT company_code, COUNT(*) AS CB
     FROM Lead_Manager
     GROUP BY company_code) B
  ON A.company_code = B.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(*) AS CC
      FROM Senior_Manager
      GROUP BY company_code) C
  ON A.company_code = C.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(*) AS CD
      FROM Manager
      GROUP BY company_code) D
  ON A.company_code = D.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(*) AS CE
      FROM Employee
      GROUP BY company_code) E
  ON A.company_code = E.company_code
ORDER BY A.company_code;
 
-- 왜 틀렸을까 생각함
```

```sql
Your Output (stdout) (Sample)
C1 Angela 2 5 13 53
C10 Earl 1 2 3 13
C100 Aaron 2 4 10 25
C11 Robert 1 1 1 3
C12 Amy 2 6 14 44
C13 Pamela 2 5 14 60
```



```sql
-- 다시 전체를 확인해보니 중복이 있음....
-- 제대로 읽지 않고 하면, 시간만 더 소요된다는 것을 생각
-- *The tables may contain duplicate records.*
-- 3) 세 번째 풀기(정답)
SELECT A.company_code, A.founder, B.CB, C.CC, D.CD, E.CE
FROM Company A  
        LEFT JOIN
    (SELECT company_code, COUNT(DISTINCT lead_manager_code) AS CB
     FROM Lead_Manager
     GROUP BY company_code) B
  ON A.company_code = B.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(DISTINCT senior_manager_code) AS CC
      FROM Senior_Manager
      GROUP BY company_code) C
  ON A.company_code = C.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(DISTINCT manager_code) AS CD
      FROM Manager
      GROUP BY company_code) D
  ON A.company_code = D.company_code
        LEFT JOIN
     (SELECT company_code, COUNT(DISTINCT employee_code) AS CE
      FROM Employee
      GROUP BY company_code) E
  ON A.company_code = E.company_code
ORDER BY A.company_code;
 
/*
1) 풀고나서 검색을 해보니 이렇게 하면 안되겠다고 반성함. 
2) 하나씩 일일이 조인할 필요가 없는 게 Employee 테이블에서 이미 다 붙어 있는 상태고, Company 테이블에서 founder만 가져오면 될 일.
3) 많이 조인하면 복잡하고 헷갈림 => 불필요

*/

```

```sql
-- 네 번째 풀이(확인 후 정답)
SELECT A.company_code
       , B.founder
       , COUNT(DISTINCT lead_manager_code)
       , COUNT(DISTINCT senior_manager_code)
       , COUNT(DISTINCT manager_code)
       , COUNT(DISTINCT employee_code)
FROM Employee A 
LEFT JOIN Company B
ON A.company_code = B.company_code
GROUP BY A.company_code, B.founder
ORDER BY A.company_code;
```

