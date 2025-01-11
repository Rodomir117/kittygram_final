[![Main Taski workflow](https://github.com/rodomir117/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/rodomir117/kittygram_final/actions/workflows/main.yml)
# Проект: Kittygram
### Учебный проект *Яндекс.Практикум* курса Python-разработчик(backend)

Проект Kittygram предназначен для публикации фото котиков и только котиков, никаких собак.


## Технологии

![Django](https://img.shields.io/badge/Django-092E20?logo=django&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?logo=postgresql&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)
![Nginx](https://img.shields.io/badge/Nginx-009639?logo=nginx&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?logo=github-actions&logoColor=white)


## Запуск проекта на удаленном сервере

1. Установить docker compose на сервер:
 ```bash
    sudo apt update
    sudo apt install curl
    curl -fSL https://get.docker.com -o get-docker.sh
    sudo sh ./get-docker.sh
    sudo apt-get install docker-compose-plugin
```

2. Скачать файл [docker-compose.production.yml](https://github.com/rodomir117/kittygram_final/blob/main/docker-compose.production.yml) на свой сервер.

3. На сервере в директории с файлом **docker-compose.production.yml** создать файл  **.env**:
``` bash    
    POSTGRES_DB=имя базы
    POSTGRES_USER=владелец базы
    POSTGRES_PASSWORD=пароль базы
    DB_HOST=db
    DB_PORT=5432
    SECRET_KEY=ключ приложения django
    DEBUG=True/False
    ALLOWED_HOSTS=разрешенные хосты(your.domain.com)
```        
4. Запустить Docker compose:
``` bash
    sudo docker compose -f docker-compose.production.yml pull
    sudo docker compose -f docker-compose.production.yml down
    sudo docker compose -f docker-compose.production.yml up -d
```

5. Собрать статику и применить миграции
``` bash
    sudo docker compose -f docker-compose.yml exec backend python manage.py migrate
    sudo docker compose -f docker-compose.yml exec backend python manage.py collectstatic
    sudo docker compose -f docker-compose.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

## Автор
[**Виталий Васюков**](https://github.com/Rodomir117)