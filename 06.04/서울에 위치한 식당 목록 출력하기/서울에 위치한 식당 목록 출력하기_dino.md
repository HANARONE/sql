```sql

-- JOIN 들어갈 때 순서 갑자기 헷갈린다 : select, from, join, on, where, group by, order by
-- 소수점 3번째 자리에서 반올림이니까, ROUND에서 2번째 자리까지 보여주기로 설정
SELECT DISTINCT I.REST_ID, I.REST_NAME, I.FOOD_TYPE, I.FAVORITES, I.ADDRESS, ROUND(AVG(R.REVIEW_SCORE), 2) AS SCORE
-- INFO 테이블에
FROM REST_INFO I
-- REVIEW 테이블을 조인한다
JOIN REST_REVIEW R
-- join 
ON I.REST_ID = R.REST_ID
-- 주소가 서울로 시작하는 row 뽑아내기
WHERE I.ADDRESS LIKE '서울%'
-- GROUP BY 조건을 2개로만 했더니, 오류남
-- ORA-00937: not a single-group group function
-- 1. SUM(), AVG(), COUNT(*) 와 같은 그룹 함수를 사용하면 GROUP BY절을 추가해줘야한다.
-- 2. GROUP BY 절에는 SELECT 절에 있는 모든 column을 작성해야한다, (GROUP BY 절에는 group function 쓸 수 없다)
GROUP BY I.REST_ID, I.REST_NAME, I.FOOD_TYPE, I.FAVORITES, I.ADDRESS
ORDER BY SCORE DESC, I.FAVORITES DESC;









-- JOIN 들어갈 때 순서 갑자기 헷갈린다 : select, from, join, on, where, group by, order by
-- 소수점 3번째 자리에서 반올림이니까, ROUND에서 2번째 자리까지 보여주기로 설정
SELECT DISTINCT I.REST_ID, I.REST_NAME, I.FOOD_TYPE, I.FAVORITES, I.ADDRESS, ROUND(AVG(R.REVIEW_SCORE), 2) AS "SCORE"
-- INFO 테이블에
FROM REST_INFO I
-- REVIEW 테이블을 조인한다
JOIN REST_REVIEW R
-- join 
ON I.REST_ID = R.REST_ID
-- 주소가 서울로 시작하는 row 뽑아내기
-- WHERE I.ADDRESS LIKE '서울%'
-- GROUP BY 조건을 2개로만 했더니, 오류남
-- ORA-00937: not a single-group group function
-- 1. SUM(), AVG(), COUNT(*) 와 같은 그룹 함수를 사용하면 GROUP BY절을 추가해줘야한다.
-- 2. GROUP BY 절에는 SELECT 절에 있는 모든 column을 작성해야한다
GROUP BY I.REST_ID, I.REST_NAME
ORDER BY SCORE DESC, I.FAVORITES DESC;
```

