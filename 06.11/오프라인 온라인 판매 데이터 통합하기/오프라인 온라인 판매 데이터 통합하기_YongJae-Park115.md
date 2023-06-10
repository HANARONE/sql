``` sql
-- 제일 어려웠던 문제, 도윤이형 도움 받음
SELECT *
-- FROM절에서 필요한 데이터들만 만들어내고 전체절 SELECT에선 *로 다 뽑아낼 예정
FROM
-- 1차 FROM절에서 필요한 데이터들 다 만들어낼 예정
    (SELECT TO_CHAR(SALES_DATE, 'YYYY-MM-DD') AS SALES_DATE, 
      PRODUCT_ID, USER_ID, SALES_AMOUNT
        FROM ONLINE_SALE
        -- ONLINE_SALE 테이블에서 날짜(형식 맞춰놓음), 상품ID, 고객ID, 판매량 데이터 추출
            WHERE TO_CHAR(SALES_DATE, 'YYYY-MM') = '2022-03'
            -- FROM절 첫번째 SELECT절에 대한 조건 작성
    UNION ALL
    -- UNION ALL 사용하여 테이블 결합 (중복 포함)
    -- 여기서는 중복 제거해라 포함해라 조건 따로 없었음. UNION(중복 제거) 사용해도 정답으로 나옴.
    SELECT TO_CHAR(SALES_DATE, 'YYYY-MM-DD') AS SALES_DATE,
     PRODUCT_ID,NULL AS USER_ID, SALES_AMOUNT 
        FROM OFFLINE_SALE
        -- 위와 마찬가지로 OFFLINE_SALE에서 ONLINE_SALE과 똑같은 열의 데이터 출력
            WHERE TO_CHAR(SALES_DATE, 'YYYY-MM') = '2022-03')
        -- OFFLINE_SALE에서 SELECT한 데이터들에 대해 조건 작성
ORDER BY SALES_DATE ASC, PRODUCT_ID ASC, USER_ID ASC
-- FROM절에서 필요한 데이터들 생성하고 메인쿼리 SELECT에서 뽑아낸 데이터들에 대해
-- ORDER BY 정렬 작성

-- UNION ALL 사용시 괄호 작성
-- ((A) UNION ALL (B)) 가 아닌 (A UNION ALL B)로 괄호 표시해줌

-- 처음에는 JOIN을 어떻게 묶고 GROUP BY를 어떻게 지은 다음 조건절을 어떻게 사용해야될까만 생각했음
-- 그래도 답이 떠오르지 않아 일단 LEFT JOIN, INNER JOIN 다 해봤는데 안되고
-- 도윤형한테 UNION ALL 쓰면 된다고 배움
-- UNION ALL은 생각도 못했었음. TABLE 묶을때 아예 통합적으로 묶어버리면 UNION ALL 사용하면 될듯


```