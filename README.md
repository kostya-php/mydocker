# kostya-php/mydocker

## Описание

Сборка Docker-контейнеров для небольших проектов. Содержит сервисы:
- NGINX
- PHP
- MySQL (MariaDB)

## Инструкция по использованию

1. Копируем стандартный файл конфигурации.
```bash
cp .env-example .env
```

2. При необходимости правим версии сервисов в файлах.
```bash
mysql/Dockerfile
nginx/Dockerfile
php/Dockerfile
```

3. Редактируем файлы конфигураций **.env** и **nginx/sites/default.conf** под свои нужды. Особенно стоит обратить внимание на параметр относительного пути к папке проекта:
```bash
APP_PATH=../app
```

4. Добавляем запись в файл /etc/hosts (например для домена example.loc)
```bash
127.0.0.1   example.loc
```

5. Запускаем
```bash
docker-compose up -d
```