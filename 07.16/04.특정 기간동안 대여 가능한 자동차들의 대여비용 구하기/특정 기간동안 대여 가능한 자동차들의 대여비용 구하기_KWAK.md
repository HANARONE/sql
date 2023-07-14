특정 기간동안 대여 가능한 자동차들의 대여비용 구하기_KWAK

```SQL
-- 테이블에서 자동차 종류가 '세단' 또는 'SUV' 인 자동차 중 
-- 2022년 11월 1일부터 2022년 11월 30일까지 대여 가능하고 
-- 30일간의 대여 금액이 50만원 이상 200만원 미만인 자동차에 대해서
-- 자동차 ID, 자동차 종류, 대여 금액(컬럼명: FEE) 리스트를 출력하는 SQL문

-- 30일간의 대여 금액은 (A.DAILY_FEE * (1 - C.DISCOUNT_RATE / 100) * 30)로 나타내면 됨.
SELECT A.CAR_ID, A.CAR_TYPE, (A.DAILY_FEE * (1 - C.DISCOUNT_RATE / 100) * 30) AS FEE

FROM
CAR_RENTAL_COMPANY_CAR A
LEFT JOIN 
(   SELECT CAR_ID, 
 	-- 2022-11-01 ~ 2022-11-30 일 사이에 대여중이면 1로 나타내고, SUM으로 합쳐서 하나라도 1이면 1로 나타날 수 있도록 설정
    SUM(CASE WHEN TO_CHAR(START_DATE, 'YYYY-MM-DD') <= '2022-11-30' and TO_CHAR(END_DATE, 'YYYY-MM-DD') >= '2022-11-01' THEN 1
        ELSE 0 END) AS OK
    FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
    GROUP BY CAR_ID
) B
ON A.CAR_ID = B.CAR_ID
LEFT JOIN 
CAR_RENTAL_COMPANY_DISCOUNT_PLAN C
ON A.CAR_TYPE = C.CAR_TYPE
-- 이제 WHERE 조건만 잘 넣어주면 됨
-- 1.  SUV, 세단 중에
-- 2.  대여가능인 것들만(OK = 0) 뽑아서
-- 3.  30일 이상일 때의 할인율만 뽑아서
-- 4.  그룹화하고
-- 5.  HAVING 절에서 50만원 이상 200만원 미만인 것만 조건넣어서
-- 6.  정렬
WHERE A.CAR_TYPE IN ('SUV', '세단')
    AND B.OK = 0
    AND C.DURATION_TYPE = '30일 이상' 
GROUP BY A.CAR_ID, A.CAR_TYPE, (A.DAILY_FEE * (1 - C.DISCOUNT_RATE / 100) * 30)
HAVING (A.DAILY_FEE * (1 - C.DISCOUNT_RATE / 100) * 30) >= 500000
    AND (A.DAILY_FEE * (1 - C.DISCOUNT_RATE / 100) * 30) < 2000000
ORDER BY 3 DESC, 2 ASC, 1 DESC
;
```

