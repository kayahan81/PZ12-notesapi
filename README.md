---
# Практическое задание 12

## ЭФМО-02-25 

## Алиев Каяхан Командар оглы
---
# Информация о проекте
Подключение Swagger/OpenAPI. Автоматическая генерация документации

## Цели занятия
1.	Освоить основы спецификации OpenAPI (Swagger) для REST API.
2.	Подключить автогенерацию документации к проекту из ПЗ 11 (notes-api).
3.	Научиться публиковать интерактивную документацию (Swagger UI / ReDoc) на эндпоинте GET /docs.
4.	Синхронизировать код и спецификацию (комментарии-аннотации → генерация) и/или «schema-first» (генерация кода из openapi.yaml).
5.	Подготовить процесс обновления документации (Makefile/скрипт).


## Файловая структура проекта:

<img width="494" height="690" alt="image" src="https://github.com/user-attachments/assets/e8e6cb30-3e9a-4bd0-88c4-305381192975" />


## Ключевые компоненты

main.go - точка входа приложения

note_mem.go – in-memory репозиторий (аналог db.go для хранения данных в памяти)

repository.go – интерфейс репозитория (абстракция для работы с данными)

handlers/notes.go – обработчики HTTP-запросов

router.go – маршрутизация

note.go – модель данных (сущность)

note_service.go – бизнес-логика (service layer)

go.mod - файл модуля Go: описание зависимостей (chi v5), версия Go, имя модуля

# Примечания по конфигурации и требования

Для запуска требуется:

Go: версия 1.25.1

PostgreSQL: версия не ниже 14

<img width="841" height="232" alt="Установка Git и Go" src="https://github.com/user-attachments/assets/8e01d831-5a7f-4376-8348-9052b240aec9" />


# Команды запуска/сборки
Для запуска http нужно выполнить 4 шага:
## 1) Клонировать данный репозиторий в удобную для вас папку:
```Powershell
git clone https://github.com/kayahan81/PZ12-notesapi
```
## 2) Перейти в папку http:
```Powershell
cd PZ11-Noteapi
```
## 3) Загрузка зависимостей:
```Powershell
go mod tidy
```
## 4) Команда запуска
```Powershell
go run .
```

# Команда сборки
Для сборки бинарника и запуска .exe файла используются данные программы

```Powershell
go build -o server.exe .
server.exe
```
# Проверка работоспособности

## Базовый функционал

Скриншот работающей страницы Swagger UI

<img width="2948" height="992" alt="image" src="https://github.com/user-attachments/assets/e27c51f6-cb42-4473-b37f-6be37b5c9f82" />
<img width="2894" height="1708" alt="image" src="https://github.com/user-attachments/assets/c4307cfb-7470-4cc6-ac4b-c94c33a8b026" />
<img width="2890" height="1574" alt="image" src="https://github.com/user-attachments/assets/fdcffa63-871a-4901-803b-a9c8a779d878" />

Проверка создания таблицы, добавления задач, подключения к бд и вывода задач

<img width="1165" height="273" alt="4 запуск и проверка" src="https://github.com/user-attachments/assets/5189cec0-f0c4-47be-9b51-58c0b6b7eca2" />

## Проверочные задания

Функция ListDone

<img width="720" height="470" alt="image" src="https://github.com/user-attachments/assets/31000924-ed13-4138-acbd-17f4ecfa2c6f" />

Функция FindByID

<img width="506" height="133" alt="image" src="https://github.com/user-attachments/assets/dc837bd3-a40c-4d0a-b64a-83e205ee478c" />

Функция CreateMany

<img width="397" height="133" alt="image" src="https://github.com/user-attachments/assets/8d184a2b-632c-4295-9b81-542e9fd5569e" />

Вывод и подсчёт текущих задач 

<img width="440" height="429" alt="image" src="https://github.com/user-attachments/assets/98beaed1-1cce-452b-93f8-c54e36fdafe9" />

## Контрольные вопросы
1.	Чем отличается OpenAPI от Swagger?

2.	В чём различие подходов code-first и schema-first? Плюсы/минусы.
3.	Какие обязательные разделы содержит спецификация OpenAPI?
4.	Для чего нужны components.schemas и как их переиспользовать в responses?
5.	Что описывают аннотации @Param, @Success, @Failure, @Router, @Security?
6.	Как опубликовать Swagger UI на отдельном префиксе (/docs) и ограничить к нему доступ?
7.	Как поддерживать актуальность документации при изменениях кода?
8.	Как подключить Bearer-аутентификацию в спецификации и что изменится в UI?
