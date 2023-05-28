





```sql
-- sketch
-- 위계를 알려준 것은 COMPANY_CODE 뿐만이 아니라 FOUNDER에 의해 밑에 직원들 소속이 달라진다는 뜻이므로. GROUP BY 조건이 2개임을 알려준것

-- 내가 뽑고 싶은 column을 쉼표로 구분하여 일단 다 나열한다
-- SELECT 시에 항상 주의 사항. 문제 읽으면서 개괄적으로 column만 써두고나서 순서대로 고려.
-- 1. DISTINCT 여부
-- 2. ALIAS 사용 여부
-- 3. 테이블 JOIN 필요한지 미리 생각
-- 4. 간단한 서브쿼리로 바로 SELECT할 대상이 있는지 생각
SELECT C.COMPANY_CODE, C.FOUNDER,
-- DISTINCT 사용 : 문제 조건에 테이블에 중복 데이터가 있을 수 있다고 제시
COUNT(DISTINCT LEAD_MANAGER_CODE),
COUNT(DISTINCT SENIOR_MANAGER_CODE),
COUNT(DISTINCT MANAGER_CODE),
COUNT(DISTINCT EMPLOYEE_CODE)
-- EMPLOYEE 테이블에서 뽑을 COLUMN 이 많으니까 여기에
FROM EMPLOYEE E 
-- COMPANY 테이블을 JOIN 할거다
JOIN COMPANY C
-- JOIN 
ON E.COMPANY_CODE = C.COMPANY_CODE
-- 문제 sketch에서 생각한 포인트, GROUP BY 조건에 FOUNDER까지 2개가 들어간다
GROUP BY C.COMPANY_CODE, C.FOUNDER
-- 문제 꼼꼼히 읽어서 ORDER BY 조건까지 개괄적으로 작성하고 다시 문제 처음부터 읽으면서 JOIN , WHERE 고민.
-- 이 문제에서는 COMPANY_CODE를 그대로 SUBSTRING & DATA TYPE 변형 없이 STRING으로 ASC하게 정렬하면 끝이다. ORDER BY 조건이 간단해졌다.
-- 지금 문제 (C_1 > C_10 > C_2) vs 더 어려우려면 (C_1 > C_2 > C_10)
ORDER BY 1;
```

