



```sql
-- 여러개 뽑아낼 때, NULL 값을 채우는 NVL 함수
SELECT PT_NAME, PT_NO, GEND_CD, AGE, NVL(TLNO,'NONE') AS TLNO
-- JOIN 없이 단독 테이블 사용
FROM PATIENT
-- 12세 이하인 여자환자 라는 조건을 WHERE절에서 설정
WHERE AGE <= 12 AND GEND_CD = 'W'
-- 정렬 기준은 나이는 내림차순, 이름은 오름차순, 순서 지켜서
ORDER BY AGE DESC, PT_NAME ASC;

-- !! 문제를 꼼꼼하게 읽자 !! ""여자""환자 조건 빼먹음
-- SELECT PT_NAME, PT_NO, GEND_CD, AGE, NVL(TLNO,'NONE') AS TLNO
-- FROM PATIENT
-- WHERE AGE <= 12
-- ORDER BY AGE DESC, PT_NAME ASC;
```

