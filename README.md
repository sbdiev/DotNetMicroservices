# Микросервисная архитектура на .NET с применением CQRS, чистой архитектуры и связи, управляемой событиями

## Общая картина окончательной архитектуры

[Вставить здесь схему или диаграмму архитектуры системы]

## Составные части микросервисов

### Service catalog
- Принципы REST API и операции CRUD
- Подключение к базе данных MongoDB NoSQL при контейнеризации Docker
- Реализация открытого API Swagger

### Service Basket
- Принципы REST API и операции CRUD
- Подключение к базе данных Redis при контейнеризации Docker
- Публикация очереди BasketCheckout с использованием MassTransit и RabbitMQ
- Реализация открытого API Swagger

### Service Ordering
- Разработка CQRS и чистой архитектуры с использованием пакетов NuGet: MediatR, FluentValidation и AutoMapper.
- Использование очереди событий RabbitMQ BasketCheckout с конфигурацией MassTransit-RabbitMQ
- Подключение к базе данных SqlServer и контейнеризация
- Использование Entity Framework Core ORM и автоматическая миграция на SqlServer при запуске приложения.
- Реализация открытого API Swagger

### Service API Gateway
- Внедрение шлюзов API с помощью Ocelot
- Примеры микросервисов/контейнеров для перенаправления через шлюзы API
- Запуск нескольких различных типов контейнеров API Gateway.

## Запуск приложения
1. Склонируйте репозиторий.
2. В корневом каталоге с файлами docker-compose.yml выполните следующую команду:
    ```bash
    docker-compose -f docker-compose.yml -f docker-compose.override.yml up –d
    ```
3. Запустите микросервисы, используя следующие URL-адреса:
   - API catalog -> [http://host.docker.internal:8000/swagger/index.html](http://host.docker.internal:8000/swagger/index.html)
   - API basket -> [http://host.docker.internal:8001/swagger/index.html](http://host.docker.internal:8001/swagger/index.html)
   - API ordering -> [http://host.docker.internal:8003/swagger/index.html](http://host.docker.internal:8003/swagger/index.html)
   - API gateway -> [http://host.docker.internal:8004/Catalog](http://host.docker.internal:8010/Catalog)
   
4. Панель управления Rabbit -> [http://host.docker.internal:15672](http://host.docker.internal:15672) — guest/guest