```sql
SELECT ANIMAL_ID, NAME FROM ANIMAL_INS
    WHERE INTAKE_CONDITION = 'Sick'
    ORDER BY ANIMAL_ID
-- WHERE 조건절에서 'Sick'를 'SICK'라고 쳐서 에러 났다
-- 조건절에선 입력된 데이터값 정확히 쓰기
```