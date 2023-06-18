```SQL
-- 몇 대인지 카운팅하는 거니까 count(*) 함수, ALIAS 확인
SELECT CAR_TYPE, COUNT(*) AS CARS
-- 단일테이블
FROM CAR_RENTAL_COMPANY_CAR
-- like in 안 먹히고 regexp 정규식 사용해야한다
WHERE REGEXP_LIKE(OPTIONS, '통풍시트|열선시트|가죽시트')
GROUP BY CAR_TYPE
ORDER BY CAR_TYPE;
```

