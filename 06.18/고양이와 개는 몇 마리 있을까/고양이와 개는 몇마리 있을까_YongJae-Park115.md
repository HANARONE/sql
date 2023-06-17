```sql
SELECT ANIMAL_TYPE, COUNT(*) FROM ANIMAL_INS
-- 고양이와 개(ANIMAL_TYPE)가 각각 몇 마리(COUNT)
WHERE ANIMAL_TYPE IN ('Cat','Dog')
-- 고양이와 개만 출력
GROUP BY ANIMAL_TYPE
-- 고양이와 개로 그룹바이 해줘야 COUNT출력 가능
ORDER BY ANIMAL_TYPE
-- 고양이를 개보다 먼저 조회 -> ANIMAL_TYPE으로 ORDER BY 하면 알파벳 순으로 오름차순
```