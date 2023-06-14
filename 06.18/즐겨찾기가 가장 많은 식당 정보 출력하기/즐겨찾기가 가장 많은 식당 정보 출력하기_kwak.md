즐겨찾기가 가장 많은 식당 정보 출력하기_kwak

```SQL
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES

FROM REST_INFO

-- 다중 열 서브쿼리..
-- 그냥 FAVORITES만 같은 조건을 사용하면 안되는 이유
-- 그냥 즐겨찾기 수만 같은 다른 식당의 값이 같다고 판단되어 출력될 수도 있음
WHERE (FOOD_TYPE, FAVORITES) IN (SELECT FOOD_TYPE, MAX(FAVORITES) FROM REST_INFO GROUP BY FOOD_TYPE)

ORDER BY 1 DESC;
```

