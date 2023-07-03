이름이 있는 동물의 아이디_kwak

```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
-- 이름이 잇는 동물의 아이디 조회
WHERE NAME IS NOT NULL
ORDER BY ANIMAL_ID ASC;
```

