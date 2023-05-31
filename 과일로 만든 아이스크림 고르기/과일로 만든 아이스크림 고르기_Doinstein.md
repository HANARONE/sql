```
SELECT F.FLAVOR
    FROM FIRST_HALF F
    JOIN ICECREAM_INFO I
    ON F.FLAVOR = I.FLAVOR -- FLAVOR 컬럼으로 조인 
    WHERE F.TOTAL_ORDER > 3000 -- 총 주문이 3000보다 높은 것
        AND I.INGREDIENT_TYPE = 'fruit_based' -- 아이스크림의 주 성분이 과일
    ORDER BY F.TOTAL_ORDER DESC;
```