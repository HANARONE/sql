```SQL
SELECT DISTINCT(CAR_ID)
FROM (
            SELECT A.CAR_ID AS CAR_ID
            FROM 
                CAR_RENTAL_COMPANY_RENTAL_HISTORY A 
                LEFT JOIN 
                CAR_RENTAL_COMPANY_CAR B
                ON A.CAR_ID = B.CAR_ID
            WHERE TO_CHAR(A.START_DATE,'MM') = '10'
                AND B.CAR_TYPE = '세단'
    )
ORDER BY CAR_ID DESC;
```

