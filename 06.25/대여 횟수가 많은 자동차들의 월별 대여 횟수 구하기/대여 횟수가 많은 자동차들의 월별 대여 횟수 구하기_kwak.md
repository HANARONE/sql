

대여 횟수가 많은 자동차들의 월별 대여 횟수 구하기_kwak

```sql
-- 필요한 열만 출력하고, RECORDS는 COUNT로 구하기
SELECT TO_NUMBER(TO_CHAR(B.START_DATE, 'MM')) AS MONTH, B.CAR_ID, COUNT(*) AS RECORDS

-- 대여 시작일을 기준으로 2022년 8월부터 2022년 10월까지 총 대여 횟수가 5회 이상인 자동차들만
-- CAR_ID 와 횟수 출력
FROM (
    SELECT CAR_ID, COUNT(*) AS COUNT
    FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
    WHERE 8 <= TO_CHAR(START_DATE, 'MM') AND 10 >= TO_CHAR(START_DATE, 'MM')
    GROUP BY CAR_ID
    HAVING COUNT(*) >= 5
) A
-- A 테이블에 다시 조인해서
-- 달, car_id 기준으로 그룹화
LEFT JOIN
CAR_RENTAL_COMPANY_RENTAL_HISTORY B
ON A.CAR_ID = B.CAR_ID
WHERE 8 <= TO_CHAR(B.START_DATE, 'MM') AND 10 >= TO_CHAR(B.START_DATE, 'MM')
GROUP BY TO_NUMBER(TO_CHAR(B.START_DATE, 'MM')), B.CAR_ID
ORDER BY 1, 2 DESC;
```

