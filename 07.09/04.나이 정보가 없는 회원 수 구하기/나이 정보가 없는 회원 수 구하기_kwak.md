나이 정보가 없는 회원 수 구하기_kwak

```sql
SELECT COUNT(*) AS USERS
FROM USER_INFO
-- 나이가 없는 회원 수 구하기! AGE IS NULL
WHERE AGE IS NULL;
```

