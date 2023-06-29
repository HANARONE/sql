```sql
-- ROW_NUMBER는 중복을 허용하지 않고, DENSE_RANK/RANK 는 중복을 허용한다는 것이다.

-- DENSE_RANK/RANK의 차이점은 DENSE_RANK는 공동등수는 하나의 등수로 보고 다음 등수를 매기지만, RANK는 공동등수를 모두 포함시키고 다음 등수를 매긴다.

SELECT CATEGORY, PRICE AS MAX_PRICE, PRODUCT_NAME
    FROM (SELECT RANK() OVER(PARTITION BY CATEGORY ORDER BY PRICE DESC) AS N,
                 CATEGORY, PRODUCT_NAME, PRICE
          FROM FOOD_PRODUCT
          WHERE CATEGORY IN ('과자', '국', '김치', '식용유'))
WHERE N = 1
ORDER BY PRICE DESC;
```

