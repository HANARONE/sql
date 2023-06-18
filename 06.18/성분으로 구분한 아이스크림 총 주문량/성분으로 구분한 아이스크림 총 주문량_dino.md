```sql
-- I 테이블과 H 테이블에서 뽑아올 것과 ALIAS 확인
SELECT I.INGREDIENT_TYPE, SUM(H.TOTAL_ORDER) AS TOTAL_ORDER
FROM FIRST_HALF H
-- H 테이블에 I 테이블을 조인
JOIN ICECREAM_INFO I
-- join 조건
ON H.FLAVOR = I.FLAVOR
-- 아이스크림 성분 별로 총주문량을 확인하고 싶으므로 group by
GROUP BY INGREDIENT_TYPE
-- 정렬조건
ORDER BY TOTAL_ORDER;
```

