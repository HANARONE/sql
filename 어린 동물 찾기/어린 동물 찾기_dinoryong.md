



```sql
-- 여러개를 뽑아내려면 쉼표로
SELECT ANIMAL_ID, NAME
-- JOIN 없이 단독 테이블
FROM ANIMAL_INS
-- where 절에 
WHERE INTAKE_CONDITION != 'Aged'
ORDER BY ANIMAL_ID;

-- 내가 mysql 이랑 가장 헷갈리는 syntax : ORACLE에서 NOT의 위치 기억
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE NOT INTAKE_CONDITION = 'Aged'
ORDER BY ANIMAL_ID;

-- 아무 생각 없이 Aged 를 대문자로 AGED로 써서 틀렸다ㅎㅎㅎㅎ
-- !! 문제를 꼼꼼하게 읽자
-- SELECT ANIMAL_ID, NAME
-- FROM ANIMAL_INS
-- WHERE INTAKE_CONDITION != 'AGED'
-- ORDER BY ANIMAL_ID;

```

