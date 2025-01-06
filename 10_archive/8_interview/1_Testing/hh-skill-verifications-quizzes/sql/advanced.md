## SQL — продвинутый уровень

🏆 Правильных ответов: 14 из 15.

#### Q1. Получите список имен и фамилий сотрудников, которые работают в отделе маркетинга, из таблицы Employees.

| Employees  |  |
|---|---|
| employee_id  | Integer  |
|  first_name | String  |
| last_name |  String |
|  department | String  |
|  job_title | String  |
|  salary | Integer  |

- [x] `SELECT first_name, last_name FROM Employees WHERE department = 'Marketing';`

#### Q2. Добавьте новый столбец email с типом данных VARCHAR(255) в существующую таблицу Clients.

- [x] `ALTER TABLE Clients ADD email VARCHAR(255);`

#### Q3. Каким будет результат выполнения следующего кода для таблицы Cars, если car_id — первичный ключ? На изображении — элементы вывода таблицы.
`INSERT INTO Cars VALUES distributor_id = 5, car_model = 'BMW X5 M50d';`

|  Cars     |         |
| -------------- | ------- |
| car_id         | Integer |
| distributor_id | Integer |
| car_model      | String  |
| number         | Integer |

Записи в таблице Cars

| car_id | distributor_id | car_model              | number |
| ------ | -------------- | ---------------------- | ------ |
| 1      | 1              | BMW X5 M50d           | 10     |
| 2      | 2              | Mercedez-Benz C-Class | 7      |
| 3      | 3              | Lexus LX               | 7      |


- [x] Отобразится ошибка

#### Q4. Вы хотите найти заработную плату отделов, у которых общая заработная плата не превышает 700 000 рублей, в таблице Salaries. Какая ошибка допущена в запросе?

```
SELECT department_id, SUM(salary) AS total_salary FROM Salaries
HAVING total_salary <= 700000 GROUP BY department_id;
```

| Salaries      | |
| ------------- | ---- |
| salary_id     | Integer |
| employee_id   | Integer |
| department_id | Integer |
| salary        | Double |

- [x] Используется total_salary <= 700000 вместо SUM(salary) <= 700000

#### Q5. Найдите данные, относящиеся только к левой таблице Orders, в таблицах Orders и Clients, учитывая, что общий столбец между ними — client_id.
| Orders | |
| --------- | ------- |
| order_id  | Integer |
| client_id | Integer |
| date      | Date    |


| Clients | |
| --------- | ------- |
| client_id    | Integer |
| company_name | String  |
| email        | String  |
| phone        | Double  |

- [x] `SELECT Orders.order_id FROM Orders LEFT JOIN Clients ON Clients.client_id = Orders.client_id WHERE Clients.client_id IS NULL;`

#### Q6. Найдите имена сотрудников, зарплата которых ниже медианной зарплаты всех сотрудников в таблице Employees.

| Employees  |         |
| ------------- | ------- |
| employee \_id | Integer |
| first_name    | String  |
| last_name     | String  |
| department    | String  |
| job_title     | String  |
| salary        | Integer |

- [x] `SELECT first_name, last_name FROM Employees WHERE salary < (SELECT MEDIAN(salary) FROM Employees);`

#### Q7. Вам нужно создать представление с именем PeopleView с данными из двух таблиц Respondents и Info, в котором будут содержаться возраст, телефоны и адреса респондентов. Какая ошибка допущена в запросе?

```
CREATE VIEW PeopleView 
AS SELECT age, phone_number, address 
FROM Respondents, Info
WHERE Respondents.respondent_id = Info.respondent_id;
```

|  Respondents  |         |
| -------------- | ------- |
| respondent_id  | Integer |
| city           | String  |
| age            | Integer |
| phone_number   | String  |
| know_languages | Array   |

|   Info  |         |
| ------------- | ------- |
| info_id       | Integer |
| respondent_id | Integer |
| phone_number  | String  |
| address       | String  |

- [x] Нужно указывать, из каких таблиц взяты данные, т. е. Respondents.age, Respondents.phone_number, Info.address

#### Q8. Вы создали некластеризованный индекс в таблице Products для столбца category, который содержит его записи и адреса соответствующей строки (в основной таблице), в которой находится запись столбца. Какой шаг из перечисленных ниже не совершается при запуске следующего запроса?

```
CREATE INDEX product_category_index

ON Products (category);

SELECT product_name, category, price

FROM Products

WHERE category = 'electronics';
```

|   Products    |         |
| ------------------- | ------- |
| product_id          | Integer |
| product_name        | String  |
| product_subcategory | String  |
| category            | String  |
| price               | Double  |

- [x] Сохранение выбранных значений в дополнительной таблице

#### Q9. Вы создали таблицу:

```
CREATE TABLE yourtable(x int NOT NULL, y int NOT NULL, CONSTRAINT pk_yourtable PRIMARY KEY(x, y));
```

Выберите, какая команда должна быть первой в процедуре, работающей с ошибками и транзакциями.

- [x] SET XACT_ABORT, NOCOUNT ON

#### Q10. У вас есть таблица Orders с миллионом строк и проиндексированным столбцом order_date, который был создан с использованием следующего запроса:

```
CREATE INDEX order_index ON Orders(order_date);
```

Каким образом вы будете оптимизировать производительность запроса, который извлекает информацию о последнем заказе для клиента из таблицы?

- [x] Использую подзапрос, чтобы получить последний order_date для клиента, а затем объединю результаты с таблицей Orders, чтобы получить полную информацию о заказе

#### Q11. Напишите SQL-запрос, который выберет все записи из таблицы Customers, у которых имя (name) начинается на букву "A" или "M", и возраст (age) больше 25 лет. Отсортируйте список в порядке убывания возраста.

- [x] ```SELECT * FROM Customers
WHERE (name LIKE 'A%' OR name LIKE 'M%') AND age > 25
ORDER BY age DESC```

#### Q12. Вы даете разрешение или запрет на выполнение определенных операций над объектами базы данных компании. Какие операторы вы используете в данном процессе?

- [x] GRANT, REVOKE

#### Q13. Какую задачу может решать данный код?

```
SELECT product_name,
CASE WHEN (price > 100) THEN 'expensive'
ELSE 'cheap'
END AS product_cost
FROM cd.database;
```

- [x] Получение данных о дорогих и дешевых товарах, где дорогими считаются товары дороже 100 рублей. При этом отобразится таблица с названием товаров в одном столбике и указанием дорогой он или дешевый в другом.

#### Q14. Вам нужен отсортированный в алфавитном порядке список из 10 неповторяющихся имён в таблице group_A. С помощью какого кода может быть решена данная задача?

- [x] ↓
```
SELECT distinct surname
FROM group_A
ORDER BY surname
LIMIT 10; 
```

#### Q15. У вас есть две таблицы: workers и salary. Первая содержит уникальный id сотрудника, его фамилию (surname) и должность (position). Во второй таблице указано: id должности, сама должность и соответствующая ей зарплата. Вам нужно узнать, сколько зарабатывает каждый сотрудник. Какой вариант кода сможет решить данную задачу?

- [x] ```SELECT *
FROM workers w JOIN salary s ON w.position = s.position;```
