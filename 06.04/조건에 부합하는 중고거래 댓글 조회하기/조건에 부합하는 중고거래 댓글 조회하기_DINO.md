```sql


# 댓글 생성일, 글 작성일
-- join테이블의 column 구분 잘 하기, oracle에서 DATE type에는 반드시 TO_CHAR
SELECT B.TITLE, B.BOARD_ID, R.REPLY_ID, R.WRITER_ID,R.CONTENTS, TO_CHAR(R.CREATED_DATE,'YYYY-MM-DD') AS CREATED_DATE
-- 게시글 테이블에
FROM USED_GOODS_BOARD B
-- 댓글 테이블을 조인
JOIN USED_GOODS_REPLY R
-- join key(?)
ON B.BOARD_ID = R.BOARD_ID
-- DATE type 에는 반드시 TO_CHAR 한 후에 뭘 한다
WHERE TO_CHAR(B.CREATED_DATE, 'YYYY-MM') = '2022-10'
-- 정렬 조건은 문제 읽을 때 미리 써두기
ORDER BY R.CREATED_DATE, B.TITLE;
```

