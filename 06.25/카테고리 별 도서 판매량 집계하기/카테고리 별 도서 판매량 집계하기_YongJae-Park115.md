```sql

SELECT A.CATEGORY, SUM(B.SALES) AS TOTAL_SALES
FROM BOOK A, BOOK_SALES B
WHERE A.BOOK_ID = B.BOOK_ID AND TO_CHAR(B.SALES_DATE,'YYYY-MM') = '2022-01'
GROUP BY A.CATEGORY
ORDER BY A.CATEGORY

-- 처음에 WHERE 조건에 A.BOOK_ID = B.BOOK_ID 안해서 틀림
```