```sql
SELECT NAME 
    FROM (SELECT ROWNUM AS RN, NAME
        FROM (SELECT * FROM ANIMAL_INS ORDER BY DATETIME ASC)
         )
    WHERE RN = 1

-- ROWNUM을 통해 순서를 정해주기 위해 FROM절 서브쿼리(인라인뷰) 사용
-- 인라인뷰 안에 인라인뷰를 한번 더 사용해 ROWNUM과 NAME 출력
-- 인라인뷰를 한번만 사용하면 WHERE절에 ROWNUM = 1 밖에 출력이 안되지만
-- 위와같이 두번 사용하면 ROWNUM AS RN -> RN = 2, 3, 4 ... 다른 숫자도 출력이 된다
```