# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Magento 2.4.7 Community Edition with Hyva theme implementation. E-commerce platform with custom modules for FAQ management and checkout customization.

## Technology Stack

- **Magento:** 2.4.7 Community Edition
- **PHP:** 8.2/8.3
- **Frontend:** Hyva theme with TailwindCSS 3.4.1 + AlpineJS 3.x
- **Database:** MySQL 5.7
- **Search:** Elasticsearch 7.7.1
- **Cache:** Redis + Varnish
- **Queue:** RabbitMQ
- **Environment:** Docker Compose

## Essential Commands

### Build & Compile

```bash
# Magento compilation and deployment
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento setup:static-content:deploy -f
bin/magento indexer:reindex
bin/magento cache:clean

# Hyva theme build (from /app/design/frontend/Roman/CustomHyva/web/tailwind/)
npm run build-prod    # Production build
npm run watch         # Development watch mode
npm run browser-sync  # Live reload development
```

### Testing & Code Quality

```bash
# Code quality checks
vendor/bin/php-cs-fixer fix              # Auto-fix code style (PSR-2)
vendor/bin/phpcs                         # Check coding standards
vendor/bin/phpstan analyse               # Static analysis
vendor/bin/phpcpd                        # Detect code duplication

# Testing
vendor/bin/phpunit                       # Run unit tests
vendor/bin/mftf run:test                 # Functional tests
```

### Development

```bash
# Docker environment
docker-compose up -d                     # Start all services
docker-compose exec php-fpm bash         # Enter PHP container
docker-compose logs -f php-fpm           # View PHP logs

# Cache management
bin/magento cache:clean                  # Clean cache
bin/magento cache:flush                  # Flush cache storage
vendor/bin/cache-clean.js --watch        # Watch mode cache cleaning

# Development mode
bin/magento deploy:mode:set developer    # Enable developer mode
```

## Architecture & Structure

### Custom Modules

```
/app/code/
├── Macademy/
│   ├── Minerva/           # FAQ management module
│   │   ├── Controller/    # Frontend controllers
│   │   ├── Model/         # Data models and resource models
│   │   ├── Setup/         # Data patches
│   │   └── etc/           # Module configuration
│   └── CustomCheckout/    # Checkout customizations
│       └── etc/           # Module configuration
```

### Theme Structure

```
/app/design/frontend/Roman/CustomHyva/
├── web/
│   └── tailwind/
│       ├── tailwind.config.js    # TailwindCSS configuration
│       ├── package.json           # NPM dependencies
│       └── tailwind-source.css   # Source styles
├── Magento_Theme/                # Theme overrides
└── etc/
    └── view.xml                  # Theme configuration
```

### Key Patterns

1. **Module Registration:** Each module requires `registration.php` and `etc/module.xml`
2. **Dependency Injection:** Use constructor injection, avoid ObjectManager
3. **Data Patches:** Database changes via `Setup/Patch/Data/` classes
4. **UI Components:** Admin grids use UI component XML definitions
5. **Frontend Rendering:** Hyva uses Alpine.js for interactivity, avoid jQuery

## Development Workflow

### Creating New Features

1. **New Module:** Create under `/app/code/{Vendor}/{Module}/` with proper registration
2. **Database Changes:** Use declarative schema (`etc/db_schema.xml`)
3. **Admin Features:** Implement ACL, menu items, and UI components
4. **Frontend Changes:** Edit in theme directory, use TailwindCSS utilities
5. **After Changes:** Run compilation, deploy static content, clear cache

### Hyva Theme Development

- **Templates:** Override in `/app/design/frontend/Roman/CustomHyva/`
- **Styles:** Use Tailwind utilities, edit `tailwind-source.css` for custom styles
- **JavaScript:** Use Alpine.js components, avoid jQuery
- **Build:** Run `npm run watch` in theme's tailwind directory during development

## Critical Files & Locations

- **Main Config:** `/app/etc/env.php` - Database, cache, session configuration
- **Module Status:** `/app/etc/config.php` - Enabled/disabled modules
- **Docker Setup:** `/docker-compose.yml` - Service definitions
- **PHP Config:** `.php-cs-fixer.dist.php` - Code style rules
- **Theme Build:** `/app/design/frontend/Roman/CustomHyva/web/tailwind/package.json`

## Known Issues & Gotchas

1. **Module.xml Typo:** Minerva module has "Meganto" instead of "Magento" in dependencies
2. **Security:** Encryption keys in env.php should be moved to environment variables
3. **Cache:** Always clear after configuration changes
4. **Permissions:** Ensure proper permissions on `var/`, `pub/static/`, `generated/`
5. **Static Deploy:** Required after any theme changes

## Docker Services

- **nginx:** Web server (port 80)
- **php-fpm:** PHP 8.2 with Xdebug
- **mysql:** Database (port 3306)
- **redis:** Cache and sessions (port 6379)
- **elasticsearch:** Search engine (port 9200)
- **varnish:** Full page cache (port 8080)
- **rabbitmq:** Message queue (port 15672)
- **mailhog:** Email testing (port 8025)
- **adminer:** Database UI (port 8082)

## Quick Debugging

```bash
# View logs
tail -f var/log/system.log
tail -f var/log/exception.log
docker-compose logs -f php-fpm

# Clear everything
rm -rf generated/* var/cache/* var/page_cache/* var/view_preprocessed/*
bin/magento setup:upgrade && bin/magento setup:di:compile && bin/magento setup:static-content:deploy -f
```