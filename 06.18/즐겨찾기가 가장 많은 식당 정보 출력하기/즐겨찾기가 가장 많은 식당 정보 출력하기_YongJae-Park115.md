```sql
SELECT FOOD_TYPE, REST_ID, REST_NAME, FAVORITES
-- 음식종류별로 즐겨찾기수가 가장 많은 식당의 음식 종류(FOOD_TYPE), ID(REST_ID), 식당 이름(REST_NAME), 즐겨찾기수(FAVORITES)를 조회
FROM REST_INFO
WHERE (FOOD_TYPE, FAVORITES) IN (
-- 음식종류별로 즐겨찾기수가 가장 많은 식당
-- WHERE 조건 절에서 음식종류, 즐겨찾기 수가 가장 많은 행을 뽑아서 조건 비교
    SELECT FOOD_TYPE, MAX(FAVORITES)
-- 음식종류(FOOD_TYPE), 즐겨찾기 수(MAX(FAVORITE))가 가장 많은 행
    FROM REST_INFO
    GROUP BY FOOD_TYPE
-- 종류별로 즐겨찾기 수 최고점 뽑기 위해 그룹바이
    )
ORDER BY FOOD_TYPE DESC
-- 음식 종류를 기준으로 내림차순 정렬
```