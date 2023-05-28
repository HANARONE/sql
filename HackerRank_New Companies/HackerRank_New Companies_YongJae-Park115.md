```sql
SELECT A.COMPANY_CODE, A.FOUNDER,
       COUNT(DISTINCT B.LEAD_MANAGER_CODE),
    --    SELECT절 COLUMN 연결 할 떄 콤마 잘 찍기
       COUNT(DISTINCT B.SENIOR_MANAGER_CODE),
       COUNT(DISTINCT B.MANAGER_CODE),
       COUNT(DISTINCT B.EMPLOYEE_CODE)
    --    복붙 할때 SELECT절 마지막 COLUMN 콤마 빼기 신경 쓸 것
-- C_k FOUNDER에 걸려있는 LM 명수, LM에 걸려있는 SM 명수, SM에 걸려있는 M명수, M에 걸려있는 EMPLOYEE 명수 출력
-- 왜 있는진 모르겠으나 칼럼 모두 똑같은 값을 가진 중복 행들이 종종 있으므로 DISTINCT로 중복 제거
FROM COMPANY A LEFT OUTER JOIN EMPLOYEE B
    ON A.COMPANY_CODE = B.COMPANY_CODE
    -- FROM 테이블1 LEFT (OUTER) JOIN 테이블2 ON 조건
GROUP BY A.COMPANY_CODE, A.FOUNDER
--  GROUP BY로 그룹화 한 칼럼은 SELECT 절에서 뽑아줘야 함
ORDER BY A.COMPANY_CODE
;
-- ORACLE 마지막에 세미콜론 찍기

-- SQL은 기본적으로 조건절로 결합하든 JOIN절로 결합하든 테이블을 하나로 묶어두고 값을 찾아야 한다
-- 처음에 생각없이 A, B 테이블 두개 꽂아두고 각각 테이블에서 값만 추출하려 했음
-- 두개 이상의 테이블 사용할거면 하나의 테이블로 묶어주고 값 추출할 것

-- 문제에서 C_1, C_10, C_2로 되지 않고 C_1, C_2, ... , C_10 형식으로 쿼리 짜라는 건줄 알았는데 C_1, C_10, C_2처럼 나오게 짜라는 건가 보다
-- C_1, C_2, ... , C_10 순으로 나오게 쿼리 짜기
ORDER BY LENGTH(A.COMPANYCODE) ASC, A.COMPANY CODE ASC


```