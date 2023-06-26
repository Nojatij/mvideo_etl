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
