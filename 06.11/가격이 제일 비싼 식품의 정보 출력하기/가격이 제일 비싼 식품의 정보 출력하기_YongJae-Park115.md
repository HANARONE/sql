```sql
SELECT PRODUCT_ID, PRODUCT_NAME, PRODUCT_CD, CATEGORY, PRICE
-- 열 전체 출력
FROM (SELECT ROWNUM AS  NUM , A.*
-- ROWNUM을 첫번째 인라인뷰에서 설정해주고 AS 붙여야 됨
FROM (SELECT * FROM FOOD_PRODUCT ORDER BY PRICE DESC) A
-- 두번째 인라인뷰에서 가격순으로 정렬
) B
WHERE B.NUM=1
-- ROWNUM = 1 만 쓸거면 간략하게 작성해도 상관 없지만
-- ROWNUM = 2,3,... 1이 아닌 숫자로 쓰는 경우 FROM절 두번 작성해줘야 되더라
```