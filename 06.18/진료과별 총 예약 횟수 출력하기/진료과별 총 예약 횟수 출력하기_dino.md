```sql
-- ALIAS 확인, ''이 아니라 "" 입력 !
SELECT MCDP_CD AS "진료과코드", COUNT(APNT_YMD) AS "5월예약건수"
FROM APPOINTMENT
-- where 조건
WHERE TO_CHAR(APNT_YMD, 'YYYY-MM') = '2022-05'
-- 진료과 코드 기준으로 group by
GROUP BY MCDP_CD
ORDER BY 2, 1;
```

