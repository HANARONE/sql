SELECT PT_NAME,PT_NO,GEND_CD,AGE,NVL(TLNO,'NONE') AS TLNO -- NVL(TLNO,'NONE') > TLNO 컬럼 중 NULL 값은 'NONE'로
    FROM PATIENT
    WHERE AGE <= 12 -- AGE가 12 이하
        AND GEND_CD = 'W' -- GEND_CD가 W(여자)인
    ORDER BY AGE DESC, PT_NAME; -- AGE 기준 내림차순 후 PT_NAME 기준 오름차순 정렬