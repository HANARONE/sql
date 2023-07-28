이름에 el이 들어가는 동물 찾기_kwak

```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
-- 개이면서 이름에 'el'이 들어가는 경우 (대문자 포함일 수 도 있으니 lower로 변환)
WHERE ANIMAL_TYPE = 'Dog' AND LOWER(NAME) LIKE '%el%'
ORDER BY NAME;
```

