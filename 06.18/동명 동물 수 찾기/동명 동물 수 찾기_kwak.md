동명 동물 수 찾기_kwak

```sql
SELECT NAME, COUNT(*) AS COUNT
FROM ANIMAL_INS
--일단 이름없는 동물은 제외해야 하므로 is not null
WHERE NAME IS NOT NULL
--동명 동물의 이름 횟수를 찾아야 하므로 name을 기준으로 그룹
GROUP BY NAME 
--동명 조건 = 같은 이름이 2회 이상인 조건
HAVING COUNT(*) >= 2
ORDER BY 1 ASC;
```

