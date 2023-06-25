식품분류별 가장 비싼 식품의 정보 조회하기_KWAK

```sql
SELECT CATEGORY, PRICE AS MAX_PRICE, PRODUCT_NAME
FROM FOOD_PRODUCT
-- 1) WHERE 서브 쿼리
-- 서브쿼리에서 카테고리 별로 가장 높은 가격 출력
-- 카테고리와 가격(MAX(PRICE))이 같은 조건
WHERE (CATEGORY, PRICE) IN 
    (
    SELECT CATEGORY, MAX(PRICE)
    FROM FOOD_PRODUCT
		-- 단, 식품 분류가 과자, 국, 김치, 식용유인 경우
        -- REGEXP_LIKE
    WHERE REGEXP_LIKE(CATEGORY, ('과자|국|김치|식용유'))
    GROUP BY CATEGORY
    )
ORDER BY 2 DESC;
```

