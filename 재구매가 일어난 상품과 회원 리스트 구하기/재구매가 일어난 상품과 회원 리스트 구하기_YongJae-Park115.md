``` sql
-- 코드를 입력하세요
SELECT USER_ID, PRODUCT_ID
FROM ONLINE_SALE
GROUP BY USER_ID, PRODUCT_ID
HAVING COUNT(PRODUCT_ID) >= 2
-- 처음에 having조건절을 생각 못하고 where절로 푸려다가 생각이 더 꼬이고 못품
-- group by 하면 해빙절 쓰면 됨됨
ORDER BY USER_ID ASC, PRODUCT_ID DESC

-- 한번에 못 풀었음
--  GROUPING하고 안에 조건은 HAVING절
```