# Техническое обеспечение и администрирование геоинформационных систем в деятельности ООПТ

## 1. Развертывание и настройка ArcGIS Enterprise
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

### Шаг 1.

[Установка PostreSQL](https://metanit.com/sql/postgresql/1.1.php)

### Шаг 2.

[Настраиваем подключения через файл pg_hba.conf](http://postgrespro.ru/docs/postgrespro/10/auth-pg-hba-conf)

Файл по умолчанию находится в директории, которая была указана при установке PostreSQL для хранения базы данных.

[Наш рабочий файл pg_hba.conf](http://gisoopt.by/gis/data/temp/pg_hba.rar)

