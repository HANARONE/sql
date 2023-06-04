





```sql

-- 서브쿼리에서 아예 name만 뽑을거라, 메인쿼리는 *(all) 로 정했다.
SELECT * FROM
-- 서브쿼리에서 내가 원하는 varchar type의 name만 뽑아낸다
    (SELECT NAME
		-- join 없이 단독 테이블
     FROM ANIMAL_INS
		-- DATETIME ASC로 정렬하면 가장 낮은 날짜 즉 과거 순서대로 정렬해준다
     ORDER BY DATETIME)
-- 서브쿼리에서 뽑아낸 결과들 중에서 ROWNUM 으로 1개만 뽑으면 보호시작일이 가장 과거인 동물만 뽑아낸다
WHERE ROWNUM <= 1;




```

