```sql
SELECT B.INGREDIENT_TYPE, SUM(A.TOTAL_ORDER) AS TOTAL_ORDER
-- 상반기 동안 각 아이스크림 성분 타입, 성분 타입에 대한 아이스크림의 총주문량(group by 성분 타입)
    FROM FIRST_HALF A LEFT JOIN ICECREAM_INFO B
-- 두 테이블 결합
        ON A.FLAVOR = B.FLAVOR
-- flavor 같을 경우, where로 결합해도 됨
    GROUP BY B.INGREDIENT_TYPE
-- select 절에 있는 ingredient_type으로 그룹바이
    ORDER BY A.TOTAL_ORDER ASC
-- 총 주문량으로 순서화
```