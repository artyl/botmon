# botmon
Telegram Bot для доставки алерт сообщении с информационных систем и систем мониторинга подписчикам
---

Перед сборкой билда необходимо отредактировать следуцющие переменные в файле .config

**BOT_TOKEN** - токен бота, получается при создании бота с помощь @BotFather'a

**BOT_USER** - имя бота, получается там же (см. выше)

**BOT_PWD** - пароль, для регистрации пользователя


---
#Собираем докер:

_docker build -t <имя докера> ._


Перед запуском докера необходимо подготовить базу данных:

Создаем docker volume:    

_docker volume create botmon_vol_ 

Помещаем в него файл с пустой БД (находится в каталоге ../sqlite) :

_cp ../sqlite/botmon.db  /var/lib/docker/volumes/botmon_vol/_data/_

Запускаем Докер : 

_docker run -d --name botmon --mount source=botmon_vol,target=/usr/local/botmon/sqlite -p 8226:8226 <имя докера>_


