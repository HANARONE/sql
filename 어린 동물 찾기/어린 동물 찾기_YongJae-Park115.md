```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS 
    WHERE INTAKE_CONDITION NOT IN ('Aged')
    ORDER BY ANIMAL_ID ASC

-- 마찬가지로 조건절에서 입력값 정확히 쓰기 'AGED'(X) 'Aged'(O)
-- WHERE COLUMN NOT IN ('입력값')
--                IN
```