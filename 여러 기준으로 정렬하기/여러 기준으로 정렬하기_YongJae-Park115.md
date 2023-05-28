```SQL
SELECT ANIMAL_ID, NAME, DATETIME FROM ANIMAL_INS
    ORDER BY NAME, DATETIME DESC
-- ORDER BY 에 두가지 기준으로 정렬
-- NAME 오름차순 먼저 정렬하고 동점값 있을시 DATETIME 내림차순 정렬
-- 오름차순엔 ASC 생략 가능 
-- 보호를 나중에 시작한 값이 우선 나와야 하므로
-- 보호를 나중에 시작했다 (날짜가 더 후년이다 -> 날짜값이 크다) -> 큰값 우선 출력 DESC

-- SELECT ANIMAL_ID, NAME, DATETIME FROM ANIMAL_INS
--     ORDER BY NAME ASC, DATETIME DESC
```