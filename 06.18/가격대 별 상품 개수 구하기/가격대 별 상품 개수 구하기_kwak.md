가격대 별 상품 개수 구하기_kwak

```SQL
SELECT TRUNC(PRICE, -4) AS PRICE_GROUP, COUNT(*) AS PROUCTS
FROM PRODUCT
-- TRUNC 쓸 수 있냐고 묻는 문제
/* 
  TRUNC(nmb, 1) -- 소수점 첫째 절사
, TRUNC(nmb, 2) -- 소수점 둘째 절사
, TRUNC(nmb,-1) -- 1단위 절사
, TRUNC(nmb,-2) -- 10단위 절사
*/
GROUP BY TRUNC(PRICE, -4)
ORDER BY 1;
```

