경기도에 위치한 식품창고 목록 출력하기_kwak

```sql
SELECT WAREHOUSE_ID,
        WAREHOUSE_NAME,
        ADDRESS,
        --  냉동시설 여부 NULL인 경우 'N'으로 출력
        NVL(FREEZER_YN,'N') AS FREEZER_YN
FROM FOOD_WAREHOUSE
-- 경기도에 위치한
WHERE ADDRESS LIKE '경기도%'
ORDER BY 1 ASC;
```

