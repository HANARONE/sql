```SQL
-- "차종"에 대해서가 아니라 "개별 차" 각각에 대해서 average_fee를 알고싶으므로 group by 없이 그냥 count (*) 하면 된다
SELECT ROUND((SUM(DAILY_FEE) / COUNT(*)), 0) AS AVERAGE_FEE
-- 단일테이블
FROM CAR_RENTAL_COMPANY_CAR
-- where 조건
WHERE CAR_TYPE = 'SUV';
```

