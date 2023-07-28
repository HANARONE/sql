중성화 여부 파악하기_kwak

```sql
SELECT
    ANIMAL_ID,
    NAME,
-- 중성화인 경우 'O'라고 표시하는 case문 만들기
    CASE WHEN SEX_UPON_INTAKE LIKE '%Neutered%' THEN 'O'
         WHEN SEX_UPON_INTAKE LIKE '%Spayed%'THEN 'O'
         ELSE 'X'
         END AS 중성화
FROM ANIMAL_INS
ORDER BY ANIMAL_ID;
```

