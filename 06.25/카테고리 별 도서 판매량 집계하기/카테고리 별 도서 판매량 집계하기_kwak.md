카테고리 별 도서 판매량 집계하기_kwak

```sql
-- total 이므로 sum
SELECT B.CATEGORY, SUM(A.SALES) AS TOTAL_SALES

-- book_sales table과 book table book_id를 기준으로 left join
FROM BOOK_SALES A
LEFT JOIN
BOOK B
ON A.BOOK_ID = B.BOOK_ID

-- 2022년 1월에 판매한 책만
WHERE TO_CHAR(A.SALES_DATE, 'YYYY-MM') = '2022-01' 
GROUP BY B.CATEGORY
ORDER BY B.CATEGORY;
```

