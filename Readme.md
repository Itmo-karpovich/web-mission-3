# Mission 3

## Part 1

[Link to video](https://jmp.sh/mVXOBYUg)

## Part 2

[Link to video](https://jmp.sh/7sOUIdWN)

## Part 3

### 1. Получение списка юзернеймов пользователей

```
SELECT username 
FROM users;
```

### 2. Получение количества отправленных сообщений каждым пользователем

```
SELECT
u.username,
COUNT(m.id) AS "number of sent messages"
FROM
users u
JOIN
messages m ON u.id = m.sender_id
GROUP BY
u.username
ORDER BY
COUNT(m.id) DESC;
```

### 3. Получение пользователя с максимальным количеством полученных сообщений

```
SELECT
u.username,
COUNT(m.id) AS "number of received messages"
FROM
users u
JOIN
messages m ON u.id = m.receiver_id
GROUP BY
u.username
ORDER BY
COUNT(m.id) DESC
LIMIT 1;
```

### 4. Получение среднего количества сообщений на пользователя

```
SELECT
AVG(message_count) AS "average messages per user"
FROM (
SELECT
COUNT(m.id) AS message_count
FROM
users u
JOIN
messages m ON u.id = m.sender_id
GROUP BY
u.id
) AS user_message_counts;
```






