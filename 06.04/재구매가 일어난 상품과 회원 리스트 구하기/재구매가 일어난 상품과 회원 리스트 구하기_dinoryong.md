```sql
-- as 조건 없음
SELECT USER_ID, PRODUCT_ID
-- join 업이 단독 테이블
FROM ONLINE_SALE
-- 동일한 회원이 동일한 상품을 구매한 것을 보기위해 group by
GROUP BY PRODUCT_ID, USER_ID
-- 재구매니까 2번 이상 구매
HAVING COUNT(*) >= 2
-- 문제 읽으면서 정렬 기준까지 쓰기
ORDER BY 1, 2 DESC;
```

