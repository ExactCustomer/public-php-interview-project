# Exact Customer: PHP Exercise

## Goal

This is a short exercise to show how you work. It covers reading and writing PHP, reading and writing SQL, and following a spec. It isn't a test of deep expertise. Use whatever tools you normally use, including AI.

Expect it to take less than 60 minutes. We'll review your work together afterward and talk through your choices.

## Task

Build a PHP endpoint or page that takes an employee and an action, and returns:

1. **Manager:** the employee's direct manager.
2. **Direct reports:** everyone who reports directly to the employee.
3. **Everyone below:** the employee's full reporting tree, with each person's level.

Examples:

- Manager of **Ben Walsh**: Priya Patel
- Direct reports of **David Okafor**: Priya Patel, Tom Becker
- Everyone below **Tom Becker**: Chloe Martin, Daniel Reyes (level 1)

JSON, formatted text or HTML  output is fine. No login or styling needed.

Don't use a framework or library. This is meant to be a simple proof of concept that shows you can put this together in plain PHP.

## Data

One table, `employees`. Each row has an `id`, `first_name`, `last_name`, `title`, `timezone`, `active` flag, and `manager_id`. The CEO has no manager.

## Running it locally

Use either database option.

### Option A: SQLite

No database server needed. Create the database from the included file:

```
sqlite3 employees.db < sqlite.sql
```

Connect from PHP with `new PDO('sqlite:employees.db')`.

### Option B: MySQL in Docker

Start a temporary MySQL 8 container:

```
docker run --rm -d --name php-test -p 3306:3306 -e MYSQL_ALLOW_EMPTY_PASSWORD=yes mysql:8
```

Wait about 20 seconds for it to start, then load the data:

```
docker exec -i php-test mysql < mysql.sql
```

Connect from PHP with `new PDO('mysql:host=127.0.0.1;port=3306;dbname=php_test;charset=utf8mb4', 'root', '')`. Use `127.0.0.1`, not `localhost`, so PHP connects over the Docker port instead of a local socket.

When you're done, `docker stop php-test` removes the container and its data.

### Serving your code

Run PHP's built-in server from your project folder:

```
php -S localhost:8000
```

## Submitting

Submit via git, you can fork this repo and commit your work, or create your own git repo and share it.  Include a short README with how to run your code. Send us the link, or give us access if the repo is private.


