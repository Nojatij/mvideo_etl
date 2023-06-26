# Блок 1. SQL
![Таблица](https://github.com/Nojatij/mvideo_etl/assets/26605856/7db87a6b-393e-43ef-9f81-b7efcd95ed40)

### 1)	Вывести список сотрудников, получающих заработную плату большую чем у непосредственного руководителя
```
select a.*
from   employee a, employee b
where  b.id = a.chief_id
and    a.salary > b.salary
```
### 2)	Вывести список сотрудников, получающих максимальную заработную плату в своём отделе
```
select a.*
select a.*
from   employee a
where  a.salary = ( select max(salary) from employee b
                    where  b.department_id = a.department_id )
```
### 3)	Вывести список ID отделов, количество сотрудников в которых не превышает 3 человек
```
select department_id
from   employee
group  by department_id
having count(*) <= 3
```
### 4)	Вывести список сотрудников, не имеющих назначенного руководителя, работающего в том-же отделе
```
select a.*
from   employee a
left   join employee b on (b.id = a.chief_id and b.department_id = a.department_id)
where  b.id is null
```
### 5)	Найти список ID отделов с максимальной суммарной зарплатой сотрудников
```
with sum_salary as
  ( select department_id, sum(salary) salary
    from   employee
    group  by department_id )
select department_id
from   sum_salary a       
where  a.salary = ( select max(salary) from sum_salary ) 
```
### 6)	Скрипт
```
Тут скрипт
```
# Блок 2. Python
### 1)	Написать функцию is_prime, принимающую 1 аргумент — число от 0 до 1000, и возвращающую True, если оно простое, и False - иначе.
```
def is_prime(number):
    flag = number > 1 and (number % 2 != 0 or number == 2) and (number % 3 != 0 or number == 3)
    i = 5;
    x = 2;

    while flag and i * i <= number:
        flag = number % i != 0
        i += x
        x = 6 - x
    return flag
```  
### 2)	Написать функцию square, принимающую 1 аргумент — сторону квадрата, и возвращающую 3 значения (с помощью кортежа): периметр квадрата, площадь квадрата и диагональ квадрата.
```
def square(side):
    perimeter = side * 4
    area = side ** 2
    diagonal = side * 2**0.5 
    return perimeter, area, diagonal
```
### 3)	Пользователь делает вклад в размере a рублей сроком на years лет под 10% годовых (каждый год размер его вклада увеличивается на 10%. Эти деньги прибавляются к сумме вклада, и на них в следующем году тоже будут проценты). Написать функцию bank, принимающая аргументы a и years, и возвращающую сумму, которая будет на счету пользователя.
```
def bank(a, years):
    for _ in range(years):
        a += a * 0.1
    return a
```
