# Post Service

## Описание

Микросервис для управления постами в веб-приложении **CorporationX**. Отвечает за создание текстовых постов, систему комментариев под постами, систему лайков (для постов и комментариев), а также организацию постов в альбомы по тематике.

## Реализованные фичи

### 1. Система альбомов постов
У пользователей веб-приложения CorporationX есть возможность организовывать посты (не только свои, но и посты других пользователей) в альбомы. Альбом — это подборка постов, сходных по тематике или наполнению, либо просто собрание любимых постов пользователя. Реализована фильтрация альбомов (по названию, диапазону дат), избранные альбомы, а также валидация владения альбомом/постом при добавлении, удалении и обновлении.

- [`AlbumController`](src/main/java/faang/school/postservice/controller/AlbumController.java)
- [`AlbumServiceImpl`](src/main/java/faang/school/postservice/service/impl/AlbumServiceImpl.java)
- [`AlbumFilterServiceImpl`](src/main/java/faang/school/postservice/filter/service/AlbumFilterServiceImpl.java)
- [`AlbumFilter`](src/main/java/faang/school/postservice/filter/album/AlbumFilter.java) — интерфейс фильтра (реализации: [`TitleFilter`](src/main/java/faang/school/postservice/filter/album/TitleFilter.java), [`FromDateFilter`](src/main/java/faang/school/postservice/filter/album/FromDateFilter.java), [`BeforeDateFilter`](src/main/java/faang/school/postservice/filter/album/BeforeDateFilter.java))
- [`AlbumRepository`](src/main/java/faang/school/postservice/repository/AlbumRepository.java)

**Технологии:** Spring Data JPA (нативные запросы), [`Feign Client`](src/main/java/faang/school/postservice/client/UserServiceClient.java), Lombok, JUnit 5 + Mockito

### 2. Swagger для post_service
В сервис подключён и настроен Swagger (OpenAPI) — интерактивная документация REST API, которая позволяет разработчикам и пользователям изучить функциональность API, протестировать эндпоинты и сгенерировать клиентский код для взаимодействия с сервисом.

- [`build.gradle.kts`](build.gradle.kts) — подключена зависимость `springdoc-openapi-starter-webmvc-ui`
- [`PostServiceApp`](src/main/java/faang/school/postservice/PostServiceApp.java) — аннотация `@OpenAPIDefinition` с описанием API

**Технологии:** SpringDoc OpenAPI (springdoc-openapi-starter-webmvc-ui)
