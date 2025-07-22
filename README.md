# Magento 2 Project with Hyvä Themes

This is a Magento 2 eCommerce platform utilizing the high-performance Hyvä frontend theme. The project is containerized using Docker for a consistent and reproducible development environment.

## Table of Contents

- [Core Technologies](#core-technologies)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
  - [1. Clone the Repository](#1-clone-the-repository)
  - [2. Start the Docker Environment](#2-start-the-docker-environment)
  - [3. Install Dependencies](#3-install-dependencies)
  - [4. Install Magento](#4-install-magento)
- [Development](#development)
  - [Magento CLI](#magento-cli)
  - [Frontend Development](#frontend-development)
  - [Database Access](#database-access)
  - [Running Tests](#running-tests)
  - [Code Quality](#code-quality)
- [Docker Environment](#docker-environment)
  - [Services](#services)
  - [Useful Commands](#useful-commands)
- [Project Structure](#project-structure)
- [License](#license)

## Core Technologies

- **Backend:** PHP / Magento 2 (v2.4.7)
- **Frontend:** Hyvä Themes (utilizing Alpine.js & Tailwind CSS)
- **Database:** MySQL 5.7
- **Search:** Elasticsearch 7.7
- **Caching:** Redis, Varnish
- **Message Queue:** RabbitMQ
- **Development Environment:** Docker / Docker Compose

## Prerequisites

Before you begin, ensure you have the following installed on your local machine:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Composer](https://getcomposer.org/download/)

## Getting Started

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd <your-project-directory>
```

### 2. Start the Docker Environment

This project includes Docker Compose configurations for different operating systems.

- **For Linux:** `docker-compose -f docker-compose.yml -f docker-compose.dev.linux.yml up -d`
- **For macOS:** `docker-compose -f docker-compose.yml -f docker-compose.dev.mac.yml up -d`
- **Generic:** `docker-compose up -d`

This will build and start all the necessary services (PHP-FPM, Nginx, MySQL, etc.) in the background.

### 3. Install Dependencies

Install the required PHP and Node.js dependencies using Composer and npm.

```bash
# Install PHP dependencies
docker-compose exec phpfpm composer install

# Install Node.js dependencies (if any)
docker-compose exec node npm install
```

### 4. Install Magento

If this is a fresh setup, you will need to run the Magento installer. The database credentials and other necessary details can be found in your `docker-compose.yml` and `app/etc/env.php` files.

**Note:** The following is an example command. You may need to adjust the values based on your `app/etc/env.php` configuration.

```bash
docker-compose exec phpfpm bin/magento setup:install \
--base-url=http://localhost/ \
--db-host=db \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=Admin \
--admin-lastname=User \
--admin-email=user@example.com \
--admin-user=admin \
--admin-password=password123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1
```

If Magento is already installed, simply run the upgrade commands:

```bash
docker-compose exec phpfpm bin/magento setup:upgrade
docker-compose exec phpfpm bin/magento setup:di:compile
docker-compose exec phpfpm bin/magento setup:static-content:deploy -f
```

## Development

### Magento CLI

To run any Magento command, execute it within the `phpfpm` container:

```bash
docker-compose exec phpfpm bin/magento <command>

# Example: Clear the cache
docker-compose exec phpfpm bin/magento cache:flush
```

### Frontend Development

This project uses Hyvä Themes, which relies on Tailwind CSS. To watch for changes and automatically recompile assets during development, you may need to run a watch script. Check the `package.json` or Hyvä documentation for the specific command.

With BrowserSync configured, your browser should automatically reload upon changes.

### Database Access

The Docker environment includes **Adminer**, a database management tool. You can access it at [http://localhost:8090](http://localhost:8090).

- **Server:** `db`
- **Username:** `magento`
- **Password:** `magento`
- **Database:** `magento`

### Running Tests

To run the PHPUnit test suite:

```bash
docker-compose exec phpfpm vendor/bin/phpunit
```

### Code Quality

This project is set up with tools to maintain code quality.

- **PHP CodeSniffer (PHPCS):**
  ```bash
  docker-compose exec phpfpm vendor/bin/phpcs
  ```

- **PHP Code Sniffer Fixer (PHPCBF):**
  ```bash
  docker-compose exec phpfpm vendor/bin/phpcbf
  ```

- **PHPStan (Static Analysis):**
  ```bash
  docker-compose exec phpfpm vendor/bin/phpstan analyse
  ```

## Docker Environment

### Services

The `docker-compose.yml` file defines the following services:

| Service         | Description                               | Ports (Host:Container) |
|-----------------|-------------------------------------------|------------------------|
| `nginx`         | Nginx web server                          | `80:8000`              |
| `phpfpm`        | PHP-FPM 8.2 processor                     | -                      |
| `db`            | MySQL 5.7 database                        | `3306:3306`            |
| `redis`         | Redis for caching                         | -                      |
| `varnish`       | Varnish Cache                             | `8080:80`              |
| `elasticsearch` | Elasticsearch 7.7 for catalog search      | `9200:9200`            |
| `rabbitmq`      | RabbitMQ for message queuing              | `5672:5672`, `15672:15672` |
| `mailhog`       | Email testing tool                        | `8025:8025` (Web UI)   |
| `adminer`       | Database management tool                  | `8090:8080`            |
| `node`          | Node.js container for frontend tasks      | `35729:35729`          |

### Useful Commands

- **Start all services:** `docker-compose up -d`
- **Stop all services:** `docker-compose down`
- **Execute a command in a container:** `docker-compose exec <service_name> <command>`
- **View logs:** `docker-compose logs -f <service_name>`

## Project Structure

- `app/code/`: Contains custom Magento modules.
- `app/design/frontend/`: Contains custom Hyvä themes.
- `app/etc/`: Main Magento configuration files.
- `bin/magento`: The Magento command-line interface.
- `composer.json`: PHP dependencies.
- `docker-compose.yml`: Docker service definitions.
- `package.json`: Node.js dependencies.
- `pub/`: The web server's document root.
- `var/`: Temporary files, cache, logs, and generated code.
- `vendor/`: Composer-managed dependencies.

## License

This project is licensed under the OSL-3.0 and AFL-3.0 licenses. See the `LICENSE.txt` and `LICENSE_AFL.txt` files for more details.
