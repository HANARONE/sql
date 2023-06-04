```SQL
-- oracle에서 날짜형은 꼭 TO_CHAR 작업 거쳐주기!
SELECT BOOK_ID, TO_CHAR(PUBLISHED_DATE,'YYYY-MM-DD')
-- 단일 테이블
FROM BOOK
-- where 조건에서 EXTRACT(YEAR FROM COLUMN)형태로 연도 뽑아내기
WHERE CATEGORY = '인문' AND
EXTRACT(YEAR FROM PUBLISHED_DATE) = '2021'
-- 정렬조건은 문제 읽을 때 미리 적어두기
ORDER BY 2;
```

