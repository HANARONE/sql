``` sql
SELECT A.REST_ID, A.REST_NAME, A.FOOD_TYPE, A.FAVORITES, A.ADDRESS, ROUND(RS, 2) AS SCORE
FROM REST_INFO A INNER JOIN 
     (SELECT REST_ID, AVG(REVIEW_SCORE) AS RS FROM REST_REVIEW       GROUP BY REST_ID) B
     ON A.REST_ID = B.REST_ID
-- FROM 절을 어떻게 합쳐야 할까 생각이 많았음.
-- 어차피 메인쿼리에서 SELECT로 뽑아내는건 대부분 A절에 있으니
-- B절에서 REST_ID GROUP BY 해서 뽑고 조인으로 결합하고자 함.
-- 동시에 REVIEW_SCORE의 그룹화된 평균값을 뽑아주면서 메인쿼리에서 써먹음
WHERE SUBSTR(ADDRESS,1,2) = '서울'
-- 서울 위치 조건 확인
ORDER BY SCORE DESC, A.FAVORITES DESC

-- 금주 헷갈렸던 문제 중 하나
-- ROUND(COLUMN, n(소수점 n의 자리수까지 출력))
-- SUBSTR(COLUMN, 시작위치, 길이)
-- INSTR(문자, 찾는 특정 문자, 시작점, n)
--  -> 주어진 문자에서 찾는 특정 문자를 시작점부터 n번째에 나오는 위치
-- 조건 확인 잘하기
-- GROUP BY 설정을 어느절에서 어떻게 하고 테이블간 JOIN을 어떤 방식으로 하는지가 중요한 문제라고 생각.
```