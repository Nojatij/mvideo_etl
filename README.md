# Задача на C#

*Напишите на C# библиотеку для поставки внешним клиентам, которая умеет вычислять площадь круга по радиусу и треугольника по трем сторонам. Дополнительно к работоспособности оценим:*

 *- Юнит-тесты*
 
 *- Легкость добавления других фигур*
 
 *- Вычисление площади фигуры без знания типа фигуры*
 
 *- Проверку на то, является ли треугольник прямоугольным"*
 
 ### Решение задачи:
[ТУТ](https://github.com/Nojatij/Mindbox/tree/master/areaOfFigures) находится класс

[ТУТ](https://github.com/Nojatij/Mindbox/tree/master/Tests) находятся тесты

# Задача на SQL

*В базе данных MS SQL Server есть продукты и категории. Одному продукту может соответствовать много категорий, в одной категории может быть много продуктов. Напишите SQL запрос для выбора всех пар «Имя продукта – Имя категории». Если у продукта нет категорий, то его имя все равно должно выводиться.*

###  Создание структуры БД:
```
 CREATE TABLE categories (
    categories_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    categories_name VARCHAR(50)
    );    
 
 CREATE TABLE products (
    products_id	INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    products_name VARCHAR(255) NOT NULL,
    categories_id INT,
    FOREIGN KEY (categories_id)  REFERENCES categories (categories_id)
    );
```
###  Заполнение базы данных:
```
    INSERT INTO categories(categories_name) VALUES ('Вода'), ('Канцелярия'), ('Еда'), ('Для кухни');
    INSERT INTO products(products_name, categories_id) VALUES ('Газировка', 1), ('Бумага', 2), ('Ножницы', 2 ), ('Ножницы', 4), ('Ложка', 4), ('Мастер и Маргарита', NULL);
```

### Вывод ответа:
```
 SELECT products_name AS Имя_Продукта, categories_name AS Имя_Категории
 FROM 
     products LEFT JOIN categories USING(categories_id)
 ORDER BY products_name;
```
