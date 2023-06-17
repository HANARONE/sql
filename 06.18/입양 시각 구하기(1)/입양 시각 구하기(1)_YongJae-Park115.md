```sql
SELECT TO_NUMBER(TO_CHAR(DATETIME, 'HH24')) AS HOUR, COUNT(*) AS COUNT
-- 각 시간대별(TO NUMBER(TO_CHAR~))로 입양이 몇 건(COUNT)이나 발생했는지 조회
-- TO_CHAR 해서 시간 뽑아낸 후 TO_NUMBER 다시 해줘야되는거 몰랐음
-- 09를 9로 바꿔줘야될것 같다고 생각했는데 방법 몰라서 검색함 -> 숫자형으로 변경
FROM ANIMAL_OUTS
WHERE TO_CHAR(DATETIME, 'HH24') BETWEEN 09 AND 19
-- 09:00부터 19:59까지
GROUP BY TO_CHAR(DATETIME, 'HH24')
-- 시간대별로 COUNT해야 하므로 시간대 GROUP BY
ORDER BY TO_CHAR(DATETIME, 'HH24') ASC
-- 시간대 순으로 정렬
```