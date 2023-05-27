```sql
-- 한 해에 탈퇴를 1번하고 가입을 2번 한 사람 있다면 => distinct user 써야 하는데 * 도 통과한다. 걍 이 문제는 범위를 rough 하게 준 듯
SELECT COUNT(DISTINCT USER_ID) AS USERS
-- join 할 테이블 없이 단독 테이블
FROM USER_INFO
-- !!! JOINED column은 data type이므로 to_char 함수로 문자형 변환 후에 => 문자 추출을 해야한다
-- !!! 날짜형 자료를 문자열로 명확하게 포멧을 지정해서 변경해야 
WHERE TO_CHAR(JOINED,'YYYY') = '2021'
-- 중첩 조건문
AND AGE BETWEEN 20 AND 29;


-- 2번째 방법 EXTRACT 사용. 이것도 date type에 쓸 수 있다.
-- SELECT COUNT(DISTINCT USER_ID) FROM USER_INFO
-- WHERE EXTRACT(YEAR FROM JOINED) = 2021 AND 20 <= AGE AND AGE <= 29;

-- SUBSTR 은 문자열을 찾으므로 => 결과는 나오나 0 return
-- SELECT COUNT(DISTINCT USER_ID) AS USERS 
-- FROM USER_INFO
-- WHERE SUBSTR(JOINED,1,4) = '2021'
-- AND AGE BETWEEN 20 AND 29;

-- JOINED에는 문자열이 없으니 => 결과는 나오나 0 return 
-- SELECT COUNT(*)    
-- FROM USER_INFO
-- WHERE 19<AGE AND 30>AGE AND JOINED like '2021%';
```

