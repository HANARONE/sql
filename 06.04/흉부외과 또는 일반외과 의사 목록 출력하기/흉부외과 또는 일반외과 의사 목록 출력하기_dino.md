```sql
-- oracle에서 날짜는 TO_CHAR 작업이 0번0번0번!
SELECT DR_NAME, DR_ID, MCDP_CD, TO_CHAR(HIRE_YMD,'yyyy-mm-dd')
-- 단일테이블
FROM DOCTOR
-- 조건이 이거나 이면 되니까 IN 써서 한 줄에 쓰고 싶었다
WHERE MCDP_CD IN ('CS', 'GS')
-- 정렬 기준 문제 읽으면서 다 쓰기
ORDER BY HIRE_YMD DESC, DR_NAME ASC;
```

