



```sql
-- 여러 개 뽑아내려면 쉼표로 구분
SELECT ANIMAL_ID, NAME
-- JOIN 없이 단독 테이블
FROM ANIMAL_INS
-- ! 조건이기 때문에 정확하게 일치하는 문자 써야함. 대소문자 구분 주의 !
WHERE INTAKE_CONDITION = 'Sick'
-- 정렬 기준은 ANIMAL_ID 1개뿐임
ORDER BY 1;
```

