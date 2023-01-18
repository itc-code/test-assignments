# Тестовое задание для стажера в юнит Merchant Experience

Задача разработать сервис, через который продавцы смогут передавать нам свои товары пачками в формате excel (xlsx).
UI делать не нужно, достаточно только API.

Сервис принимает на вход ссылку на файл и id продавца, к чьему аккаунту будут привязаны загружаемые товары.
Сервис читает файл и сохраняет, либо обновляет товары в БД. Обновление будет происходить, если пара (id продавца, offer_id) уже есть у нас в базе.
В ответ на запрос выдаёт краткую статистику: количество созданных товаров, обновлённых, удалённых и количество строк с ошибками (например цена отрицательная, либо вообще не число).

Для проверки работоспособности сервиса нужно так же реализовать метод, с помощью которого можно будет достать список товаров из базы.
Метод должен принимать на вход id продавца, offer_id, подстрока названия товара (по тексту "теле" находились и "телефоны", и "телевизоры"). Ни один параметр не является обязательным, все указанные параметры применяются через логический оператор "AND".

В каждой строке скачанного файла будет содержаться отдельный товар.
Колонки в файле и соответствующие значения полей товара следующие:

* **offer_id** уникальный идентификатор товара в системе продавца
* **name** название товара
* **price** цена в рублях
* **quantity** количество товара на складе продавца
* **available** true/false, в случае false продавец хочет удалить товар из нашей базы


### Наши ожидания

* язык программирования Go
* предоставлена инструкция по запуску приложения. В идеале (но не обязательно) – использовать контейнеризацию с возможностью запустить проект командой docker run/docker-compose up
* в качестве БД использована Postgres
* код выложен на github

### Усложнения

* написаны тесты
* проведено нагрузочное тестирование с целью понять, с какой скоростью сервис может переваривать файлы
* реализована асинхронная схема работы, т.е. сервис принимает запрос, сразу возвращает id задания и в отдельной горутине начинает его выполнять. Клиент может узнать статус задания отдельным запросом.