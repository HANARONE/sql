```sql
SELECT MCDP_CD AS "진료과코드", COUNT(APNT_YMD) AS "5월예약건수"
--  2022년 5월에 예약한 환자 수(COUNT)를 진료과코드 별(MCDP_CD)로 조회
FROM APPOINTMENT
WHERE TO_CHAR(APNT_YMD, 'YYYY-MM') = '2022-05'
-- 2022년 5월(WHERE 날짜)에 예약한 환자 수를 진료과코드 별로 조회
GROUP BY MCDP_CD
-- 2022년 5월에 예약한 환자 수를 진료과코드 별(GROUP BY MCDP_CD)로 조회
ORDER BY COUNT(APNT_YMD) ASC, MCDP_CD ASC
-- 진료과별 예약한 환자 수를 기준으로 오름차순 정렬
```