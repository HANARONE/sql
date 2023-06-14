자동차 종류 별 특정 옵션이 포함된 자동차 수 구하기_kwak

```sql
SELECT CAR_TYPE, COUNT(CAR_ID) AS CARS

--단일테이블
FROM CAR_RENTAL_COMPANY_CAR
--'통풍시트', '열선시트', '가죽시트' 중 하나 이상의 옵션이 포함된 자동차
WHERE (OPTIONS LIKE '%열선시트%' OR OPTIONS LIKE '%통풍시트%' OR OPTIONS LIKE '%가죽시트%')
--문제:자동차 종류 별로 몇 대인지?
--CAR_TYPE으로 그룹해서 COUNT(CAR_ID)하면 몇 대인지 구할 수 있음
GROUP BY CAR_TYPE

ORDER BY CAR_TYPE ASC;
```

