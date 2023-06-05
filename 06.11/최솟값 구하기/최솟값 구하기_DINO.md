```SQL
-- DATE type 명시적변환 없이 그대로 둬야함
SELECT DATETIME
-- INLINE view 로 시간이 가장 작은 ROW 뽑아낸다
FROM (SELECT DATETIME FROM ANIMAL_INS ORDER BY 1)
-- 첫번째 를 뽑아낸다
WHERE ROWNUM = 1;
```

