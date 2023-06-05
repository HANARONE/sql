```sql
-- COUNT(DISTINCT()) 와 DISTINCT(COUNT()) 는 다르다 ㅋㅋ
SELECT COUNT(DISTINCT(NAME))
FROM ANIMAL_INS
-- 빼먹기 쉬운 조건은 문제 읽으면서 바로 써두기
WHERE NAME IS NOT NULL;
```

