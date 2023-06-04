```sql
-- join하려는 테이블에서 flavor 골라옴
SELECT F.FLAVOR
-- 첫 분기 매출 테이블에
FROM FIRST_HALF F
-- INFO table에 조인한다
JOIN ICECREAM_INFO I
-- join 조건
ON F.FLAVOR = I.FLAVOR
-- 조건문, AND
WHERE TOTAL_ORDER >= 3000
AND I.INGREDIENT_TYPE = 'fruit_based'
-- 정렬조건 문제 읽을 때 다 쓰기
ORDER BY TOTAL_ORDER DESC;
```

