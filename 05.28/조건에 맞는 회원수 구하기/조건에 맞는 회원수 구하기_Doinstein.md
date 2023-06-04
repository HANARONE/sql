SELECT COUNT(*) AS USERS -- 모든 행 개수 count 후 컬럼명 USERS로 별칭
    FROM USER_INFO
    WHERE TO_CHAR(JOINED, 'YYYY') = '2021' -- JOINED 컬럼 연도 문자열로 변경 후 '2021'과 같은 행
        AND AGE BETWEEN 20 AND 29; -- AGE 컬럼 20~29사이인 행 