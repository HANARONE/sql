조건에 맞는 사용자와 총 거래금액 조회하기_kwak

```sql
SELECT B.USER_ID, B.NICKNAME, SUM(PRICE) AS TOTAL_SALES
-- USED_GOODS_BOARD TABLE A와 USED_GOODS_USER TABLE B
-- WRITER_ID 와 USER ID가 같은 조건으로 JOIN
FROM USED_GOODS_BOARD A LEFT JOIN USED_GOODS_USER B 
	ON A.WRITER_ID = B.USER_ID
-- 단, 완료된 중고거래인 경우 => WHERE STATUS = 'DONE'
WHERE STATUS = 'DONE'
GROUP BY USER_ID, NICKNAME
-- 단, 총금액이 70만 원 이상인 경우
HAVING SUM(PRICE) >= 700000
ORDER BY TOTAL_SALES;
```

