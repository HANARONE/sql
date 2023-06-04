``` sql
-- 코드를 입력하세요
SELECT ROUND(AVG(DAILY_FEE),0) AS AVERAGE_FEE 
-- ROUND(COLUMN, 소숫점 자리수) -> 반올림 함수
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = 'SUV'

-- 반올림 ROUND 기억 안났음
```