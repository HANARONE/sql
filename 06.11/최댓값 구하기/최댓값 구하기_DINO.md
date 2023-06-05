```SQL
-- 여기서 DATE type의 형태는 명시적 변환 없이 그대로 둬야함
SELECT DATETIME
-- INLINE VIEW 로 TIME 이 가장 큰 값 구해야 가장 최신 시간
FROM (SELECT DATETIME FROM ANIMAL_INS ORDER BY 1 DESC)
-- ROWNUM 으로 첫번째 값 추출
WHERE ROWNUM = 1;
```

