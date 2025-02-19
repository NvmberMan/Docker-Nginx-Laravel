# Docker Laravel Setup Guide With Nginx

This guide will help you set up a Laravel project using Docker. Please follow the instructions carefully.

## For Linux :penguin:

### 1. Clone Repository

```bash
git clone https://github.com/NvmberMan/docker-nginx-laravel.git
```

### 2. Installation

To get started, update your package index and install the necessary packages:

```bash
sudo apt update
sudo apt install make
```

### 3. Update Laravel Configuration

Open the `.env` file in your Laravel project and update the `DB_HOST` variable to `mysql`.

### 4. Run Setup

Execute the following command to set up your Docker environment:

```bash
make run-app-with-setup
```

### 5. Run Data (Optional)

If you have migrations or seeders, you can run the following command:

```bash
make run-db-migrate
```

### 6. Resolve Permission Errors (Optional)

If you encounter permission errors, run the following command:

```bash
make run-fix-permission
```

## For Windows :desktop_computer:

### 1. Clone Repository

```bash
git clone https://github.com/NvmberMan/docker-nginx-laravel.git
```

fill `src` folder with your `laravel-app`

### 2. Update Laravel Configuration

Open the `.env` file in your Laravel project and update the `DB_HOST` variable to `mysql`.

### 3. Run Setup

Execute the following command to set up your Docker environment:

```bash
docker compose build
docker compose up -d
docker exec php /bin/sh -c "composer install && npm install && chmod -R 777 storage && php artisan key:generate"
```

### 4. Run Data (Optional)

If you have migrations or seeders, you can run the following command:

```bash
docker exec php /bin/sh -c "php artisan migrate:fresh --seed"
```

### 5. Resolve Permission Errors (Optional)

If you encounter permission errors, run the following command:

```bash
docker exec php /bin/sh -c "sudo chmod -R 777 storage"
docker exec php /bin/sh -c "php artisan cache:clear"
docker exec php /bin/sh -c "php artisan config:clear"
docker exec php /bin/sh -c "php artisan config:cache"
```
