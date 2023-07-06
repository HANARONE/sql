이름이 없는 동물의 아이디_kwak

```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
-- 이름이 없는 채로 들어온 동물 ID 조회
WHERE NAME IS NULL
ORDER BY ANIMAL_ID ASC;
```

