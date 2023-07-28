오랜 기간 보호한 동물(2)_kwak

```sql
SELECT ANIMAL_ID, NAME
FROM (
        SELECT  A.ANIMAL_ID AS ANIMAL_ID,
                A.NAME AS NAME,
  -- 나간 시간에서 들어온 시간을 빼서 기간 열 만들기
                B.DATETIME-A.DATETIME AS DA 
        FROM ANIMAL_INS A, ANIMAL_OUTS B 
        WHERE A.ANIMAL_ID = B.ANIMAL_ID
        ORDER BY DA DESC
)
WHERE ROWNUM <= 2;
```

