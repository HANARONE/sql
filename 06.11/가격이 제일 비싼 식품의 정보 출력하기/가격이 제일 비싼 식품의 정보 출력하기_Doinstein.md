```sql
SELECT *
    FROM (SELECT * 
          FROM FOOD_PRODUCT 
          ORDER BY PRICE DESC)
    WHERE ROWNUM = 1;
```

