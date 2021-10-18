clone all repo

```
cd frontend-webtech-final

cp .env-example .env
```

edit .env to

```
VUE_APP_ENDPOINT=http://{host ip}:8000
VUE_APP_WEBSOCKET_ENDPOINT=http://{host ip}:3000
```

```
cd docker-compose dir

cp docker-compose.yml ../

cd ..

cd backend-webtech-final

cp .env-example .env
```

Edit .env to

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

```
composer install

open Dockerfile set GID and UID to output of id -u and id -g

cd ..

docker-compose up -d

docker exec -it backend-api php artisan key:generate

docker exec -it backend-api php artisan jwt:secret

docker exec -it backend-api php artisan storage:link

docker exec -it backend-api php artisan migrate:fresh --seed
```

frontend:localhost:80

backend:localhost:8000
