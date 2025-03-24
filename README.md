# Техническое обеспечение и администрирование геоинформационных систем в деятельности ООПТ

## 1. Развертывание и настройка ArcGIS Enterprise

Список портов, которые необходимы для работы ArcGIS Enterprise (необходимо открыть в брандмауэре):
- сервер: 6443, 6080, 6006;
- портал: 7080, 7443;
- датастор: 2443, 9876, 29080, 29081, 4369, 29079, 29085, 29090, 9220, 9320, 6443, 9829. 

[Развертывание системы ArcGIS Enterprise](https://blogs.esri-cis.com/2022/07/14/arcgis_enterprise_deployment1091/):

- [Руководство по установке ArcGIS Server 10.9.1 (Windows)](https://enterprise.arcgis.com/ru/server/10.9.1/install/windows/welcome-to-the-arcgis-for-server-install-guide.htm)
  
- [Руководство по установке Portal for ArcGIS 10.9.1 (Windows)](https://enterprise.arcgis.com/ru/portal/10.9.1/install/windows/welcome-to-the-portal-for-arcgis-installation-guide.htm)
  
- [Руководство по установке ArcGIS Data Store 10.9.1 (Windows)](https://enterprise.arcgis.com/ru/data-store/10.9.1/install/windows/welcome-to-arcgis-data-store-installation-guide.htm)
  
- [Руководство по установке ArcGIS Web Adaptor 10.9.1 (Java Platform)](https://enterprise.arcgis.com/ru/web-adaptor/10.9.1/install/java-windows/welcome-arcgis-web-adaptor-install-guide.htm)

[Подводные камни установки серверных продуктов ArcGIS](https://blogs.esri-cis.ru/2015/06/08/underwater-stones-installation-arcgis-server/)

## 2. Развертывание настройка PostgreSQL, интеграция с ArcGIS Desktop

[]()

Версии ПО в ГИС ГПУ "НП "Нарочанский":
- ArcGIS Enterprise (ArcGIS Server, Portal for ArcGIS, ArcGIS Data Store, ArcGIS Web Adaptor) все версии 10.9.1.
- PostgreSQL 10.8.
- ArcGIS Desktop 10.8 или 10.6.1.
- ArcGIS Pro 3.0.0.

Все это корректно работает между собой.

[Требования к версии PostgreSQL ПО ArcGIS оф. документация](https://enterprise.arcgis.com/ru/system-requirements/10.9.1/windows/database-requirements-postgresql.htm)

По умалчанию PostgreSQL использует порт 5432, его необходимо открыть в брандмауэре.

### Шаг 1. Установка

[Установка PostreSQL](https://metanit.com/sql/postgresql/1.1.php)

### Шаг 2. Настройка входящих подключений

[Настраиваем подключения через файл pg_hba.conf](http://postgrespro.ru/docs/postgrespro/10/auth-pg-hba-conf)

Файл по умолчанию находится в директории, которая была указана при установке PostreSQL для хранения базы данных.

[Наш рабочий файл pg_hba.conf](http://gisoopt.by/gis/data/temp/pg_hba.rar)


### Шаг 3. Добавление типа ST_Geometry в базу данных PostgreSQL

Для соединения с СУБД PostreSQL ПО ArcGIS Desktop  необходимо добавть библиотеку ST_Geometry в директорию установки PostgreSQL, для этого:
- из директории установки ArcGIS Desktop (по умолчанию c:\Program Files (x86)\ArcGIS\Desktop10.8\DatabaseSupport\PostgreSQL\) для соответсвующей версии СУБД и операционной системы скопировать файл st_geometry.dll;
- перейти в директорию установки СУБД PostreSQL (по умолчанию c:\Program Files\PostgreSQL\10\lib\) и вставить скопированую библиотеку.

Как должно выглядеть подключение к многопользовательской БД в ArcGIS Desktop / ArcGIS Pro:

![](https://github.com/a91n0d/gis_naroch/blob/main/source/connect_DB.jpg?raw=true)

где:
- 1 - Имя платформы БД;
- 2 - Адрес сервера;
- 3 - Имя пользователя и пароль;
- 4 - Выбор подключаемой БД из перечня.

## 3. Создание многопользовательской базы данных в ArcGIS Pro

### Шаг 1. Создание многопользовательской бд

Для создания базы данных зайти на вкладку *Анализ* -> *Инструменты*.
![Панель управления ArcGIS Pro](https://github.com/user-attachments/assets/7c814672-f8ed-49e6-b916-112380cb8c80)

Во вкладке *Геообработка* ввести *Создать многопользовательскую базу данных*.
![Инструменты Геообработки](https://github.com/user-attachments/assets/a36bb97c-96a2-41a5-b05c-4b1369039e15)

### Шаг 2. Последовательность операций при создание многопользовательской бд
1. в окне *Создать многопользовательскую базу* в поле *Платформа базы данных* указать PostgreSQL;
2. в поле *Экземпляр* – экземпляр БД;
3. в поле *База данных* – название базы данных;
4. в поле *Администратор базы данных* – postgres;
5. в поле *Пароль администратора базы данных* – пароль, заданный при установки PostgreSQL;
6. в поле *Пароль администратора базы данных* – повторно ввести предыдущий пароль;
7. в поле *Файл авторизации* – файл авторизации к ArcGIS Enterprise;
8. в поле *Пространственный тип* – PostGIS.



