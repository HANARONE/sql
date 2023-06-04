``` sql
-- 코드를 입력하세요
SELECT BOOK_ID, TO_CHAR(PUBLISHED_DATE, 'YYYY-MM-DD') AS PUBLISHED_DATE
-- 문제 내 주의사항 확인
-- 출력 결과 예시와 똑같이 날짜 형식 맞춰주기
FROM BOOK
WHERE TO_CHAR(PUBLISHED_DATE,'YYYY') = '2021' AND
      CATEGORY = '인문'
ORDER BY PUBLISHED_DATE ASC

-- 주의사항 확인
```