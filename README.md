### Запуск БД ###

```bash
docker run --name=todo-db -e POSTGRES_PASSWORD="query" -p 5436:5432 -d --rm postgres
```

## Создание миграций ##

Используется утилита golang-migrate

```bash
migrate create -ext sql -dir ./schema -seq init
```

## Выполнение миграций ##

# Up #

```bash
migrate -path ./schema -database 'postgres://postgres:qwerty@localhost:5436/postgres?sslmode=disable' up
```

# Down #

```bash
migrate -path ./schema -database 'postgres://postgres:qwerty@localhost:5436/postgres?sslmode=disable' down
```

## Подключение к БД через cli ##

```bash
docker exec -it todo-db bash
psql -U postgres
```

### Запуск приложения ###

```bash
go run cmd/main.go
```
