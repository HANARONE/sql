```sql
SELECT NAME, COUNT(*) AS COUNT
FROM ANIMAL_INS
-- group by 이후에 조건을 따져야함 
GROUP BY NAME
-- WHERE절 조건이 아니라 HAVING절 조건으로 해야한다
HAVING COUNT(NAME) >= 2
ORDER BY 1;
```

