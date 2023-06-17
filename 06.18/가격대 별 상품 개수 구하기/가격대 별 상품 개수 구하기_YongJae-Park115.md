```sql
SELECT TRUNC(PRICE, -4) PRICE_GROUP, COUNT(PRODUCT_ID) PRODUCTS
-- 만원 단위의 가격대 별(TRUNC)로 상품 개수(COUNT)를 출력
-- TRUNC 함수 아예 생각 못했음.
FROM PRODUCT
GROUP BY TRUNC(PRICE, -4)
-- 가격대별로 상품 개수 출력해야 하므로 TRUNC~로 묶어줌
ORDER BY TRUNC(PRICE, -4)
-- 결과는 가격대를 기준으로 오름차순
```