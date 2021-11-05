# How to use docker-compose to deploy

## Clone all repo below

FrontEnd-Vue :https://github.com/webtech-final/frontend-webtech-final

Backend-API :https://github.com/webtech-final/backend-webtech-final

Backend-Websocket :https://github.com/webtech-final/backend-tetris-websocket

## Create FrontEnd .env

```
cd frontend-webtech-final

cp .env-example .env
```

## Edit FrontEnd .env

```
VUE_APP_ENDPOINT=http://{host ip}:8000
VUE_APP_WEBSOCKET_ENDPOINT=http://{host ip}:3000
```

## Copy docker-compose.yml to ../

```
cd docker-compose dir

cp docker-compose.yml ../

cd ..
```

## Create Backend-API .env

```
cd backend-webtech-final

cp .env-example .env
```

## Edit Backend-API .env

```
APP_URL=http://{host ip}

DB_CONNECTION=mysql
DB_HOST=api-db
DB_PORT=3306
DB_DATABASE=tetris_d
DB_USERNAME=root
DB_PASSWORD=

MIX_LARAVEL_END_POINT="http://{host ip}:8000"
```

## Create Backend-Websocket .env

```
cd backend-tetris-websocket

cp .env-example .env
```

## Edit Backend-Websocket .env

```
PORT={PORT}
```

## Install API Dependency

```
composer install
```

## Edit Docker php Image User Permission

```
open Dockerfile set GID and UID to output of id -u and id -g
```

## Deploy

```
cd ..

docker-compose up -d

docker exec -it backend-api php artisan key:generate

docker exec -it backend-api php artisan jwt:secret

docker exec -it backend-api php artisan storage:link

docker exec -it backend-api php artisan migrate:fresh --seed
```

## URL

Frontend-Vue :http://{host ip}

Backend-API :http://{host ip}:8000

Backend-Websocket :http://{host ip}:3000
