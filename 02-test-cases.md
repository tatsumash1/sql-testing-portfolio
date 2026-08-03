# Тест-кейсы SQL-тестирования базы Northwind

## Структура базы

## TC-SQL-001. Проверка наличия основных таблиц Northwind

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-001 |
| Название | Проверка наличия основных таблиц Northwind |
| Связанный пункт чек-листа | Проверить наличие основных таблиц Northwind |
| Предусловия | База Northwind открыта в DB Browser for SQLite. |
| Тестовые данные | Системная таблица `sqlite_master` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить список найденных таблиц. |
| SQL-запрос | `SELECT name FROM sqlite_master WHERE type = 'table' AND name IN ('Customers', 'Orders', 'Order Details', 'Products', 'Categories', 'Suppliers', 'Employees', 'Shippers') ORDER BY name;` |
| Ожидаемый результат | Запрос возвращает все основные таблицы Northwind: `Customers`, `Orders`, `Order Details`, `Products`, `Categories`, `Suppliers`, `Employees`, `Shippers`. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-002. Проверка связи `Orders` с `Customers`

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-002 |
| Название | Проверка связи таблицы `Orders` с таблицей `Customers` |
| Связанный пункт чек-листа | Проверить, что таблица `Orders` связана с `Customers` |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблицы `Orders` и `Customers` доступны. |
| Тестовые данные | Таблицы `Orders`, `Customers`; поле `CustomerID` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT o.OrderID, o.CustomerID FROM Orders o LEFT JOIN Customers c ON o.CustomerID = c.CustomerID WHERE c.CustomerID IS NULL;` |
| Ожидаемый результат | Запрос не возвращает строк. Все заказы связаны с существующими клиентами. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-003. Проверка связи `Order Details` с `Orders`

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-003 |
| Название | Проверка связи таблицы `Order Details` с таблицей `Orders` |
| Связанный пункт чек-листа | Проверить, что таблица `Order Details` связана с `Orders` |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблицы `Order Details` и `Orders` доступны. |
| Тестовые данные | Таблицы `Order Details`, `Orders`; поле `OrderID` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT od.OrderID FROM "Order Details" od LEFT JOIN Orders o ON od.OrderID = o.OrderID WHERE o.OrderID IS NULL;` |
| Ожидаемый результат | Запрос не возвращает строк. Все строки состава заказов связаны с существующими заказами. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-004. Проверка связи `Order Details` с `Products`

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-004 |
| Название | Проверка связи таблицы `Order Details` с таблицей `Products` |
| Связанный пункт чек-листа | Проверить, что таблица `Order Details` связана с `Products` |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблицы `Order Details` и `Products` доступны. |
| Тестовые данные | Таблицы `Order Details`, `Products`; поле `ProductID` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT od.OrderID, od.ProductID FROM "Order Details" od LEFT JOIN Products p ON od.ProductID = p.ProductID WHERE p.ProductID IS NULL;` |
| Ожидаемый результат | Запрос не возвращает строк. Все товары из состава заказов существуют в таблице `Products`. |
| Статус | Manual |
| Результат | Not Run |

## Проверка заказов

## TC-SQL-005. Проверка заказов без существующего клиента

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-005 |
| Название | Проверка заказов без существующего клиента |
| Связанный пункт чек-листа | Найти заказы без существующего клиента |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблицы `Orders` и `Customers` доступны. |
| Тестовые данные | Таблицы `Orders`, `Customers`; поле `CustomerID` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT o.OrderID, o.CustomerID FROM Orders o LEFT JOIN Customers c ON o.CustomerID = c.CustomerID WHERE c.CustomerID IS NULL;` |
| Ожидаемый результат | Запрос не возвращает строк. Все заказы связаны с существующими клиентами. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-006. Проверка заказов без существующего сотрудника

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-006 |
| Название | Проверка заказов без существующего сотрудника |
| Связанный пункт чек-листа | Найти заказы без существующего сотрудника |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблицы `Orders` и `Employees` доступны. |
| Тестовые данные | Таблицы `Orders`, `Employees`; поле `EmployeeID` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT o.OrderID, o.EmployeeID FROM Orders o LEFT JOIN Employees e ON o.EmployeeID = e.EmployeeID WHERE e.EmployeeID IS NULL;` |
| Ожидаемый результат | Запрос не возвращает строк. Все заказы связаны с существующими сотрудниками. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-007. Проверка заказов без существующей службы доставки

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-007 |
| Название | Проверка заказов без существующей службы доставки |
| Связанный пункт чек-листа | Найти заказы без существующей службы доставки |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблицы `Orders` и `Shippers` доступны. |
| Тестовые данные | Таблицы `Orders`, `Shippers`; поля `ShipVia`, `ShipperID` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT o.OrderID, o.ShipVia FROM Orders o LEFT JOIN Shippers s ON o.ShipVia = s.ShipperID WHERE s.ShipperID IS NULL;` |
| Ожидаемый результат | Запрос не возвращает строк. Все заказы связаны с существующими службами доставки. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-008. Проверка заказов без товаров

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-008 |
| Название | Проверка заказов без товаров |
| Связанный пункт чек-листа | Найти заказы без товаров |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблицы `Orders` и `Order Details` доступны. |
| Тестовые данные | Таблицы `Orders`, `Order Details`; поле `OrderID` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT o.OrderID FROM Orders o LEFT JOIN "Order Details" od ON o.OrderID = od.OrderID WHERE od.OrderID IS NULL;` |
| Ожидаемый результат | Запрос не возвращает строк. Каждый заказ содержит хотя бы один товар. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-009. Проверка даты отправки заказа

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-009 |
| Название | Проверка даты отправки заказа |
| Связанный пункт чек-листа | Проверить, что дата отправки не раньше даты заказа |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблица `Orders` доступна. |
| Тестовые данные | Таблица `Orders`; поля `OrderID`, `OrderDate`, `ShippedDate` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT OrderID, OrderDate, ShippedDate FROM Orders WHERE ShippedDate IS NOT NULL AND ShippedDate < OrderDate;` |
| Ожидаемый результат | Запрос не возвращает строк. Дата отправки заказа не раньше даты создания заказа. |
| Статус | Manual |
| Результат | Not Run |

## TC-SQL-010. Проверка стоимости доставки заказа

| Поле | Значение |
| --- | --- |
| ID | TC-SQL-010 |
| Название | Проверка отрицательной стоимости доставки |
| Связанный пункт чек-листа | Проверить, что стоимость доставки не отрицательная |
| Предусловия | База Northwind открыта в DB Browser for SQLite. Таблица `Orders` доступна. |
| Тестовые данные | Таблица `Orders`; поля `OrderID`, `Freight` |
| Шаги | 1. Открыть вкладку выполнения SQL-запросов. <br> 2. Выполнить SQL-запрос. <br> 3. Проверить результат выборки. |
| SQL-запрос | `SELECT OrderID, Freight FROM Orders WHERE Freight < 0;` |
| Ожидаемый результат | Запрос не возвращает строк. Стоимость доставки не содержит отрицательных значений. |
| Статус | Manual |
| Результат | Not Run |

