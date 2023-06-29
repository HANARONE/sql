자동차 대여 기록에서 대여중 /대여 가능 여부 구분하기_kwak

```sql
-- 기본적으로 FROM절에서 1단계 처리했음

SELECT CAR_ID, 
CASE WHEN MIN(CD) = 1 THEN '대여중'
ELSE '대여 가능'
END AS AVAILABILITY
-- 1) 22년 10월 16일 사이에 대여날짜와 반납날짜가 있는 경우 1로 표기
-- 2) 아니면 2로 표시하는 열 CD 만듦
-- 이걸 그냥 사용하면 안되는 게, 1도 있고 2도 함께 표기되는 차인 경우 최종적으로 2로 표기해야 함
FROM 
  (
  SELECT CAR_ID,
  CASE WHEN TO_DATE('2022-10-16', 'YYYY-MM-DD') >= START_DATE AND TO_DATE('2022-10-16', 'YYYY-MM-DD') <= END_DATE THEN 1
  ELSE 2
  END AS CD
  FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
  )
-- 따라서 car_id를 기준으로 하돼, MIN(CD) = 1 을 넣어서 
-- 2만 있는 경우는 '대여 가능'으로 1도 있는 경우는 '대여중'으로 표시함
GROUP BY CAR_ID 
-- 정렬은 CAR_ID 기준으로 내림차순
ORDER BY 1 DESC;
```

