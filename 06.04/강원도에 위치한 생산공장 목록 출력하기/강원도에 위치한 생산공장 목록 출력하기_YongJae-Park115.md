```sql
-- 코드를 입력하세요
SELECT FACTORY_ID, FACTORY_NAME, ADDRESS FROM FOOD_FACTORY
WHERE SUBSTR(ADDRESS,0,3) = '강원도'
-- SUBSTR(COLUMN, 시작점, 끝점)
-- SQL은 파이썬과 달리 1부터 시작. 0부터 해도 상관은 없는듯
ORDER BY FACTORY_ID ASC

-- SUBSTR 특정 문자열 부터 자르기
-- INSTR 특정 문자 위치 찾기
-- INSTR(전체 문자열, 찾을 문자열, 시작위치, 발생 횟수)
-- INSTR은 특정 문자열의 위치(숫자) 파악
```