입양 시각 구하기(1)_kwak

```sql
--AS HOUR, AS COUNT 바꾸는 것 잊지 않기
SELECT TO_NUMBER(TO_CHAR(DATETIME,'HH24')) AS HOUR, COUNT(*) AS COUNT

FROM ANIMAL_OUTS
--09시 부터 20시 까지 입양된 횟수를 구해야함
--BETWEEN도 되는 것 같은데, 그냥 비교 조건 활용
--24시간 형식의 시를 기준으로 조회할 수 있도록 했고,
--그냥 TO_CHAR만 쓰면 숫자랑 비교가 안 되니, TO_NUMBER 무조건 쓰기
WHERE 9 <= TO_NUMBER(TO_CHAR(DATETIME,'HH24'))
    AND 20 > TO_NUMBER(TO_CHAR(DATETIME,'HH24'))
--시각을 기준으로 비교해야 하므로 TO_NUMBER(TO_CHAR(DATETIME,'HH24')) 그룹
GROUP BY TO_NUMBER(TO_CHAR(DATETIME,'HH24'))
ORDER BY HOUR ASC
;
```

