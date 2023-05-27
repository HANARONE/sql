



```SQL
-- 여러 개 뽑아낼 때는 쉼표로 구분
SELECT ANIMAL_ID, NAME, DATETIME
-- JOIN 없이 단독 테이블 사용
FROM ANIMAL_INS
-- 첫번째 정렬 기준은 NAME 을 먼저 쓰고
-- 두번째 정렬 기준인 DATETIME 을 DESC 정렬하면 보호일 날짜가 높은 순서, 즉 최신 순서대로 정렬된다
ORDER BY 2, 3 DESC
```

