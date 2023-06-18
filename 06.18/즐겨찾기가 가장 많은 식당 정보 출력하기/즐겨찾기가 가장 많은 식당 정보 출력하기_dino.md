```sql
-- alias 사용 x 확인, 4개 column 확인
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
FROM REST_INFO
-- '음식종류' 별 즐겨찾기 수가 가장 많은 것을 찾아야 하므로, food_type과 favorites 숫자가 똑같은 row를 찾아내야 한다
WHERE (FOOD_TYPE, FAVORITES) IN (
    SELECT FOOD_TYPE, MAX(FAVORITES)
    FROM REST_INFO
    GROUP BY FOOD_TYPE
)
-- 정렬조건
ORDER BY 1 DESC;
```

