``` sql
SELECT 
PT_NAME, PT_NO, GEND_CD, AGE, DECODE(TLNO, NULL, 'NONE', TLNO) AS TLNO
    FROM PATIENT 
    WHERE AGE <= 12 AND GEND_CD = 'W'
    ORDER BY AGE DESC, PT_NAME ASC

-- SQL 에서 조건문 사용할 때 DECODE 이용
-- DECODE(COLUMN, 조건1, 결과1, 결과 2) 
-- -> COLUMN이 조건 충족시 결과 1 출력, 그 외엔 결과 2 출력
-- DECODE(COLUMN, 조건1, 결과1, 조건2, 결과2, 조건3, 결과3 ...)
-- -> COLUMN이 조건1 충족시 결과 1 출력, 조건2 충족시 결과 2 출력, 조건3 충족시 결과3 출력...

-- NVL(COLUMN, '지정값')
-- COLUMN이 NULL인 경우 '지정값' 출력, NULL 아닐시 기존 값 그대로 출력
-- NVL2(COLUMN, '지정값', '지정값2')
-- COLUMN이 NULL인 경우 '지정값2' 출력, NULL 아닌 경우 '지정값' 출력
-- ※※※※※ NVL2 NULL 출력값 순서 유의 ※※※※※
```