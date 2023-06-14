고양이와 개는 몇 마리 있을까_kwak

```sql

SELECT ANIMAL_TYPE, COUNT(*) AS COUNT

FROM ANIMAL_INS

--고양이와 개 몇마리인지 각각 조회해야 하므로 ANIMAL_TYPE으로 묶기
GROUP BY ANIMAL_TYPE

ORDER BY 1;
```

