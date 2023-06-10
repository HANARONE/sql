``` sql
SELECT COUNT(ANIMAL_ID) FROM ANIMAL_INS
-- 주어진 테이블에서 COUNT함수를 이용하여 동물 수 세기
-- COUNT 함수 안에 * 사용해도 됨. 
-- 일부열은 NULL값을 갖고 있을 수 있어서 개수가 누락될 수 있는데 
-- 전체 행을 세면 전체가 NULL값은 아닐테고 그럼 누락될 일은 없으니까 오히려 * 사용하는게 더 좋으려나
```