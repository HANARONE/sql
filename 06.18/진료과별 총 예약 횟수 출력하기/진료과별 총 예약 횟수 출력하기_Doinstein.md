```SQL
-- 별칭에 공백이 있을 경우 쌍따옴표
-- 별칭 첫문자가 숫자일 경우 쌍따옴표
SELECT mcdp_cd AS "진료과 코드", COUNT(*) AS "5월예약건수" 
    FROM APPOINTMENT
    WHERE TO_CHAR(APNT_YMD,'YYYYMM') = '202205'
    GROUP BY mcdp_cd
    ORDER BY "5월예약건수","진료과 코드"
```

