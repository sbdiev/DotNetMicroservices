# Микросервисная архитектура на .NET с применением CQRS, чистой архитектуры и связи, управляемой событиями

## Общая картина окончательной архитектуры
![Microservice on  NETCore](https://github.com/sbdiev/DotNetMicroservices/assets/58542325/e9c14c58-3c08-4e1a-8416-9fbd7c3e1bb6)

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
   - API catalog -> [http://localhost:8000/swagger/index.html](http://localhost:8000/swagger/index.html)
   - API basket -> [http://localhost:8001/swagger/index.html](http://localhost:8001/swagger/index.html)
   - API ordering -> [http://localhost:8003/swagger/index.html](http://localhost:8003/swagger/index.html)
   - API gateway -> [http://localhost:8004/Catalog](http://localhost:8010/Catalog)
   
4. Панель управления Rabbit -> [http://localhost:15672](http://localhost:15672) — guest/guest
