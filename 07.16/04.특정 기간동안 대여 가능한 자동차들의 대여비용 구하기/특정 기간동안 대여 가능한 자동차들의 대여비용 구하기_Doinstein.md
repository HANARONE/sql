```SQL
SELECT *
FROM (SELECT DISTINCT(C.CAR_ID), C.CAR_TYPE, (C.DAILY_FEE * (100-TO_NUMBER(REGEXP_SUBSTR(D.DISCOUNT_RATE, '[^%]',1,1)))/100 * 30) AS FEE
      FROM CAR_RENTAL_COMPANY_CAR C,
           CAR_RENTAL_COMPANY_RENTAL_HISTORY R,
           CAR_RENTAL_COMPANY_DISCOUNT_PLAN D
      WHERE C.CAR_ID = R.CAR_ID 
            AND C.CAR_TYPE = D.CAR_TYPE
            AND C.CAR_TYPE IN ('세단','SUV')
            AND C.CAR_ID NOT IN (SELECT DISTINCT(car_id)
                                 FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY R
                                 WHERE TO_CHAR(START_DATE,'YYYYMMDD') <= '20221130'
                                       AND TO_CHAR(END_DATE,'YYYYMMDD') >= '20221101')  
            AND D.duration_type = '30일 이상')
WHERE 500000 <= FEE AND FEE < 2000000
ORDER BY FEE DESC, car_type, car_id DESC;
```