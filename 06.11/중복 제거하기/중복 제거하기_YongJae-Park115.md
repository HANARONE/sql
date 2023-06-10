``` sql
SELECT COUNT(DISTINCT NAME) AS COUNT FROM ANIMAL_INS
-- 주어진 테이블에서 NAME의 개수 출력하는데 DISTINCT를 사용해 중복 제거

WHERE NAME IS NOT NULL
-- 제출까지 했을때는 WHERE절 안써도 정답 떠서 몰랐는데 NAME이 NULL값이 아니라는 조건 있었음.
-- 문제 꼼꼼히 확인해야될듯
```