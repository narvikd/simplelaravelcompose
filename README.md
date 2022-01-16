# Simple Laravel Compose

## Instructions
```bash
git clone $repo # Clone
cd src # Move to source where the laravel install will reside
rm src/.keep # Remove the keep file or Compose will yell at you
composer create-project laravel/laravel . # Install a fresh copy of Laravel. (You can move your own.)
docker-compose build && docker-compose up -d # Build and start the containers. (You can use the start.sh file on the root directory.)
```

![Laravel Root](https://user-images.githubusercontent.com/84069271/149656643-70e77b8b-964b-4c67-b340-6fa64e110d4e.png)


Now edit simplelaravelcompose/src/.env and modify this:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=
```
To make it point to the mysql container, db and pass. An example is included in the root directory (laravelenv.example.env):

```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=db
DB_USERNAME=root
DB_PASSWORD=rootpass
```

### Note:
Don't use php commands locally, they're not going to work. Instead execute them directly through the php container. (PS: You don't need php artisan serve because you're already serving it.)

For example, we would execute migrations like this:
```bash
docker-compose exec php php /var/www/html/artisan migrate
```

![Laravel migration](https://user-images.githubusercontent.com/84069271/149656652-13e85d68-88cd-442b-9dd5-eb87c8bb857e.png)
