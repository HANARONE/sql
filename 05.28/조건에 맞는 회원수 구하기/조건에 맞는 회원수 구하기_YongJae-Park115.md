```sql
SELECT COUNT(*) FROM USER_INFO 
    WHERE YEAR(JOINED) = '2021'
    AND AGE BETWEEN 20 AND 29

-- 이 문제에서는 JOINED COLUMN의 데이터타입이 DATE 이기에 바로 YEAR 함수 적용이 됐지만
-- 만약 문자열 함수라면 날짜형으로 변환을 시키든 문자형으로 추출하든 일련의 과정을 거쳐야 할 것 같다
-- WHERE 조건 여러개일시 AND / OR로 연결
-- AGE 조건에서 BETWEEN 사용도 되고 >=, <=로 조건 두번 걸어도 되고

-- 프로그래머스에서 풀때는 그냥 정답처리 돼서 지금 확인했는데
-- 결과표 보니까 COUNT(*) 뒤에 AS USERS 붙여줬어야 됐다.
```