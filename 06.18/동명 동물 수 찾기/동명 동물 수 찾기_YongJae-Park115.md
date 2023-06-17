```sql
SELECT NAME, COUNT(ANIMAL_ID)
-- 동물 이름(NAME) 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수(COUNT)를 조회
FROM ANIMAL_INS
GROUP BY NAME
-- 동물 이름 중 COUNT해야 하므로 이름으로 GROUP BY
HAVING COUNT(ANIMAL_ID)>=2 AND NAME IS NOT NULL
-- 이름이 없는 동물은 집계에서 제외(NAME IS NOT NULL), 동물 이름 중 두 번 이상 쓰인 이름(COUNT>=)과
ORDER BY NAME
-- 결과는 이름 순으로 조회
```