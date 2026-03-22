# Task Service

Сервис управления задачами.

## Технологии
- Java 21
- Spring Boot 3.2.4
- Spring Data JPA
- Spring Kafka
- PostgreSQL
- Apache Kafka
- Docker

## Запуск

```bash
docker-compose up -d
```

Приложение будет доступно по адресу: `http://localhost:8080`

## API Endpoints

### Задачи

| Метод | URL | Описание |
|-------|-----|----------|
| GET | /tasks?page=0&size=10 | Получить задачи с пагинацией |
| GET | /tasks/{id} | Получить задачу по ID |
| POST | /tasks | Создать задачу |
| PATCH | /tasks/{id}/status?status=IN_PROGRESS | Сменить статус задачи |
| PATCH | /tasks/{taskId}/assignee/{userId} | Назначить исполнителя |

### Пользователи

| Метод | URL | Описание |
|-------|-----|----------|
| GET | /users | Получить всех пользователей |
| GET | /users/{id} | Получить пользователя по ID |
| POST | /users | Создать пользователя |

## Примеры запросов

### Создать задачу

```json
POST /tasks
{
    "name": "Моя задача",
    "description": "Описание задачи"
}
```

### Создать пользователя

```json
POST /users
{
    "name": "Иван Петров",
    "email": "ivan@example.com"
}
```

## События Kafka
- `task-created` - отправляется при создании задачи
- `task-assigned` - отправляется при назначении исполнителя

## Ограничения
- Поддержка до 10_000 пользователей
- Поддержка до 100_000 задач