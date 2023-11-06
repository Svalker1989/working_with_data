# Домашнее задание к занятию "`Работа с данными (DDL/DML)`" - `Стрекозов Владимир`

### Задание 1
  
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.  
1.2. Создайте учётную запись sys_temp.  
`create user 'sys_temp' identified by 'qwerty';`  
1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)  
`select host, user from mysql.user;`  
![](https://github.com/Svalker1989/working_with_data/blob/main/Z1.3.PNG)  
1.4. Дайте все права для пользователя sys_temp.  
`grant all privileges on *.* to 'sys_temp';`  
1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)   
`SHOW GRANTS FOR sys_temp;`  
Отображаются коряво в консоли, как поправить вывод не сообразил.  
![](https://github.com/Svalker1989/working_with_data/blob/main/Z1.5.PNG)  
1.6. Переподключитесь к базе данных от имени sys_temp.  
`mysql -u sys_temp -p`  
Для смены типа аутентификации с sha2 используйте запрос:  
`ALTER USER 'sys_test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';`  
1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.  
1.7. Восстановите дамп в базу данных.  
Делал командой:  
`mysql -u sys_temp -p sakila < sakila-data.sql`  
1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)  
![](https://github.com/Svalker1989/working_with_data/blob/main/Z1.8.PNG)  
Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.  
 
### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)  
   
Название таблицы | Название первичного ключа  
customer         | customer_id  
  
![](https://github.com/Svalker1989/working_with_data/blob/main/Z2.PNG)  
  
### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.  
Чтобы включить возможность частично изымать права исопльзовал команду:  
`SET PERSIST partial_revokes = ON;`  
Далее забираем права на добавление,изменение, удаление записей:  
`REVOKE INSERT,UPDATE,DELETE ON sakila.* FROM sys_temp;`  
3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)  
`SHOW GRANTS FOR sys_temp;`
![](https://github.com/Svalker1989/working_with_data/blob/main/Z3.PNG) 
