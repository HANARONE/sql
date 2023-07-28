카테고리 별 상품 개수 구하기_kwak

```sql
SELECT 
-- SUBSTR로 카테고리 만들기
-- COUNT()로 개수 구하기
       SUBSTR(PRODUCT_CODE, 1, 2) AS CATEGORY,
       COUNT(*) AS PRODUCTS
FROM PRODUCT
GROUP BY SUBSTR(PRODUCT_CODE, 1, 2)
ORDER BY CATEGORY;
```

