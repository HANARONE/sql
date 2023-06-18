```sql
-- ALIAS 사용 확인, 가격대 범위를 나누기 위해 TRUNC 함수 사용
SELECT TRUNC(PRICE, -4) AS PRICE_GROUP, COUNT(*) AS PRODUCTS
FROM PRODUCT
-- 가격대별로 갯수를 카운팅하고 싶으므로, 가격대로 group by
GROUP BY TRUNC(PRICE, -4)
-- 정렬 조건
ORDER BY 1;
```

