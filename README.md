# MYSQL

## Задание

Развернуть базу из дампа и настроить репликацию Цель: В результате выполнения ДЗ студент развернет базу из дампа и настроит репликацию. В материалах приложены ссылки на вагрант для репликации и дамп базы bet.dmp Базу развернуть на мастере и настроить так, чтобы реплицировались таблицы: | bookmaker | | competition | | market | | odds | | outcome

* Настроить GTID репликацию

варианты которые принимаются к сдаче:

- рабочий вагрантафайл
- скрины или логи SHOW TABLES * конфиги * пример в логе изменения строки и появления строки на реплике


## Выполнение ДЗ

Копируем файлы в каталог и запускаем Vagrantfile:

```shell
vagrant up
```

## Проверка:

1. Подключиться к серверу master:

```shell
 vagrant ssh master
```

- Вывести содержимое таблицы bookmaker:

```shell
mysql -e "use bet; select * from bookmaker;"
```

![image 1](https://github.com/IvanPrivalov/HW27/blob/master/screens/1.png)

![image 2](https://github.com/IvanPrivalov/HW27/blob/master/screens/2.png)

2. Добавить запись bet1 в таблицу bookmaker:

```shell
mysql -e "use bet; insert into bookmaker (id,bookmaker_name) values(1,'bet1');"
```

![image 3](https://github.com/IvanPrivalov/HW27/blob/master/screens/3.png)

3. Подключиться к серверу slave:

```shell
 vagrant ssh slave
```

4. Вывести содержимое таблицы bookmaker, убедившись, что новая запись в ней присутствует:

```shell
mysql -e "use bet; select * from bookmaker;"
```

![image 4](https://github.com/IvanPrivalov/HW27/blob/master/screens/4.png)








