```sql
SELECT CAR_TYPE, COUNT(CAR_ID) AS CARS
-- 자동차 종류 별(CAR_TYPE)로 몇 대(COUNT(CAR_ID))
    FROM CAR_RENTAL_COMPANY_CAR
    WHERE OPTIONS LIKE '%통풍시트%'
    OR OPTIONS LIKE '%가죽시트%'
    OR OPTIONS LIKE '%열선시트%'
-- OPTIONS IN ('통풍시트', '가죽시트', '열선시트') 했다가 오답처리됨.
-- IN 연산자로 사용하려면 행별로 통풍시트, 가죽시트, 열선시트 각 하나씩 입력 돼있어야함
-- 여러개의 값이 한 행에 동시에 들어가 있으므로 정규식 써줘야함
    GROUP BY CAR_TYPE
-- 차 타입 그룹바이
    ORDER BY CAR_TYPE ASC
```