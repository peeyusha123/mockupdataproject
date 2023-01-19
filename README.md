2.1)
SELECT DISTINCT email_domain
FROM users
WHERE email_domain LIKE '%.edu'
LIMIT 25;

2.2)
SELECT COUNT(user_id)
FROM users
WHERE email_domain LIKE '%.edu' AND city = 'New York';

2.3)
SELECT COUNT(user_id)
FROM users
WHERE mobile_app = 'mobile-user';

3)
SELECT COUNT(sign_up_at),
 strftime('%H', sign_up_at) AS 'Hour'
FROM users
GROUP BY 2;

4.1)
SELECT users.email_domain,
 COUNT(
 CASE
 WHEN progress.learn_cpp = 'started' OR progress.learn_cpp = 'completed' THEN users.user_id
 END) AS c_plus_plus,
 COUNT(
 CASE
 WHEN progress.learn_sql = 'completed' OR progress.learn_sql = 'started' THEN users.user_id
 END) AS sql,
 COUNT(
 CASE
 WHEN progress.learn_html = 'completed' OR progress.learn_html = 'started' THEN users.user_id
 END) AS html,
 COUNT(
 CASE
 WHEN progress.learn_javascript = 'started' OR progress.learn_javascript = 'completed' THEN 
users.user_id
 END) AS javascript,
 COUNT(
 CASE
 WHEN progress.learn_java = 'started' OR progress.learn_java = 'completed' THEN users.user_id
 END) AS java
FROM users
JOIN progress
 ON users.user_id = progress.user_id
 GROUP BY 1;
 
4.2)
SELECT users.email_domain,
 COUNT(
 CASE
 WHEN progress.learn_cpp = 'started' OR progress.learn_cpp = 'completed' THEN users.user_id
 END) AS c_plus_plus,
 COUNT(
 CASE
 WHEN progress.learn_sql = 'completed' OR progress.learn_sql = 'started' THEN users.user_id
 END) AS sql,
 COUNT(
 CASE
 WHEN progress.learn_html = 'completed' OR progress.learn_html = 'started' THEN users.user_id
 END) AS html,
 COUNT(
 CASE
 WHEN progress.learn_javascript = 'started' OR progress.learn_javascript = 'completed' THEN 
users.user_id
 END) AS javascript,
 COUNT(
 CASE
 WHEN progress.learn_java = 'started' OR progress.learn_java = 'completed' THEN users.user_id
 END) AS java
FROM users
JOIN progress
 ON users.user_id = progress.user_id
 WHERE city = 'New York'
 GROUP BY 1;
 
4.3)
SELECT users.email_domain,
 COUNT(
 CASE
 WHEN progress.learn_cpp = 'started' OR progress.learn_cpp = 'completed' THEN users.user_id
 END) AS c_plus_plus,
 COUNT(
 CASE
 WHEN progress.learn_sql = 'completed' OR progress.learn_sql = 'started' THEN users.user_id
 END) AS sql,
 COUNT(
 CASE
 WHEN progress.learn_html = 'completed' OR progress.learn_html = 'started' THEN users.user_id
 END) AS html,
 COUNT(
 CASE
 WHEN progress.learn_javascript = 'started' OR progress.learn_javascript = 'completed' THEN 
users.user_id
 END) AS javascript,
 COUNT(
 CASE
 WHEN progress.learn_java = 'started' OR progress.learn_java = 'completed' THEN users.user_id
 END) AS java
FROM users
JOIN progress
 ON users.user_id = progress.user_id
 WHERE city = 'Chicago'
 GROUP BY 1;
