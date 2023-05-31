```
SELECT FACTORY_ID, FACTORY_NAME, ADDRESS
    FROM FOOD_FACTORY
    WHERE REGEXP_SUBSTR(ADDRESS,'[^ ]+',1,1) = '강원도' -- 정규식 > 공백이 아닌 문자열 중 1번째부터 시작한 것에서 1번째
    ORDER BY FACTORY_ID
;
```