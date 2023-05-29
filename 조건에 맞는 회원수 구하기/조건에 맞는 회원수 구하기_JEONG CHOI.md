SELECT COUNT(*) AS USERS
   FROM USER_INFO
    WHERE AGE BETWEEN 20 AND 29 AND EXTRACT(YEAR FROM JOINED) = 2021;


-- COUNT(*)해서 USERS라는 컬럼으로 저장하기
-- 날짜를 가져올 때 여러 방식이 있는데 년도만 가져올 땐 EXTRACT써서 특정 년도 가저오기 가능 