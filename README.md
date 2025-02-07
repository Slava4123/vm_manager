# Система управления виртуальными машинами

Система управления виртуальными машинами с клиент-серверной архитектурой. Клиент взаимодействует с сервером для выполнения различных команд управления виртуальными машинами и их дисками.

## Содержание

- [Описание](#описание)
- [Установка](#установка)
- [Использование](#использование)
- [Команды](#команды)
- [Вклад](#вклад)
- [Лицензия](#лицензия)

## Описание

Данный проект включает в себя:
- **Сервер** (`server/server.py`): Управляет виртуальными машинами и их дисками, хранит информацию в базе данных PostgreSQL.
- **Клиент** (`client/client.py`): Позволяет пользователю вводить команды для взаимодействия с сервером.

Сервер использует PostgreSQL для хранения данных о виртуальных машинах и дисках.

## Установка

1. Убедитесь, что у вас установлен Python 3.7 или выше.

2. Установите `poetry`, если он еще не установлен:
   ```
   pip install poetry
   ```
Инициализируйте проект (если это новый проект):
```
poetry init
```
Установите зависимости проекта с помощью poetry:
```
poetry add asyncio asyncpg python-dotenv
```
Настройте переменные окружения для подключения к базе данных. Создайте файл .env в корневой директории проекта со следующими переменными:
```
DB_HOST=localhost
DB_PORT=5432
DB_USER=ваш_пользователь
DB_PASSWORD=ваш_пароль
DB_NAME=ваша_база_данных
```
Использование
Запустите сервер:
```
python -m server.server
```
Вы должны увидеть сообщение о том, что сервер запущен.

В другом терминале запустите клиент:
```
python -m client.client
```
Введите команды для взаимодействия с сервером.

Команды
Вот список доступных команд, которые вы можете использовать в клиенте:
```
AUTH <vm_id> <ram> <cpu> - Аутентификация или регистрация виртуальной машины.
ADD_VM <vm_id> <ram> <cpu> - Добавление новой виртуальной машины.
LIST_VMS - Получение списка всех активных виртуальных машин.
LIST_AUTH_VMS - Получение списка авторизованных виртуальных машин.
UPDATE_VM <id> <ram> <cpu> - Обновление параметров виртуальной машины.
LOGOUT <vm_id> - Деавторизация виртуальной машины.
LIST_DISKS - Получение списка всех дисков.
ADD_DISK <disk_id> <vm_id> <size> - Добавление диска к виртуальной машине.
REMOVE_VM <vm_id> - Удаление виртуальной машины.
REMOVE_DISK <disk_id> - Удаление диска из виртуальной машины.
CHECK_ALL_VMS - Проверка всех виртуальных машин.
```
