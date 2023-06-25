입양 시각 구하기(2)_kwak

```sql
SELECT HOUR, COUNT(B.DATETIME) AS COUNT
-- 가장 중요한 것은 0~23까지의 HOUR를 만드는 방법
-- 계층형 쿼리를 이해해야 된다는 데..
-- LEVEL은 기본적으로 1부터 시작 따라서 LEVEL-1해야 0부터 시작함
-- 여기서 CONNECT BY LEVEL <= 24로 해서 24-1 =23까지 출력되게 만듦
FROM (  SELECT LEVEL-1 AS HOUR
        FROM DUAL
        CONNECT BY LEVEL <= 24) A 
    LEFT JOIN ANIMAL_OUTS B
ON A.HOUR = TO_CHAR(B.DATETIME, 'HH24')
GROUP BY HOUR
ORDER BY HOUR ASC;
```

