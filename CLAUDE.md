# Magento 2 + Hyva Theme Project Configuration

## Project Overview

This is a Magento 2.4.7 Community Edition project with Hyva theme implementation, featuring custom modules and optimized performance stack.

## Technology Stack

### Core Platform
- **Framework:** Magento 2.4.7 Community Edition
- **PHP Version:** 8.2
- **Database:** MySQL 5.7
- **Search Engine:** Elasticsearch 7.7.1
- **Message Queue:** RabbitMQ

### Frontend Stack (Hyva)
- **Theme:** Hyva (Custom theme: Roman/CustomHyva)
- **CSS Framework:** TailwindCSS 3.x
- **JavaScript:** AlpineJS 3.x
- **Build Tools:** Node.js 14, NPM/Yarn
- **Development:** Browser-sync for hot reload

### Performance & Caching
- **Full Page Cache:** Varnish 6.x
- **Session Storage:** Redis
- **Backend Cache:** Redis
- **CDN:** Configured for static assets

### Development Environment
- **Containerization:** Docker & Docker Compose
- **Local Domain:** hyva.local (configure in hosts file)
- **Admin URL:** /admin
- **Development Mode:** Enabled for local development

## Custom Modules

### Installed Custom Modules
1. **Macademy/CustomCheckout** - Enhanced checkout experience
2. **Macademy/Minerva** - Custom product management features

## Project Structure

```
/app
  /code           # Custom modules location
    /Macademy     # Vendor namespace
      /CustomCheckout
      /Minerva
  /design
    /frontend
      /Roman      # Vendor namespace
        /CustomHyva  # Hyva child theme
/vendor           # Composer dependencies
/pub              # Web root
/var              # Generated files, cache, logs
/generated        # Generated code
```

## Development Guidelines

### Magento Best Practices
- Follow Magento 2 coding standards (PSR-12)
- Use dependency injection, avoid ObjectManager
- Create data patches for database changes
- Use declarative schema for table modifications
- Implement proper ACL for admin features
- Use plugins/preferences sparingly

### Hyva Theme Development
- Use Tailwind utility classes, avoid custom CSS
- Leverage AlpineJS for interactivity
- Keep templates lean, logic in view models
- Use Hyva's GraphQL where applicable
- Test on mobile-first approach
- Optimize images with lazy loading

### Code Quality Standards
- Run PHP CodeSniffer: `vendor/bin/phpcs`
- Run PHP CS Fixer: `vendor/bin/php-cs-fixer fix`
- Static analysis: `vendor/bin/phpstan analyse`
- Unit tests: `vendor/bin/phpunit`
- Integration tests: `dev/tests/integration`

## Common Commands

### Magento CLI
```bash
bin/magento cache:clean
bin/magento cache:flush
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento setup:static-content:deploy -f
bin/magento indexer:reindex
bin/magento deploy:mode:set developer
```

### Hyva Theme Build
```bash
cd app/design/frontend/Roman/CustomHyva
npm install
npm run build-prod   # Production build
npm run watch        # Development with hot reload
```

### Docker Commands
```bash
docker-compose up -d
docker-compose down
docker-compose exec web bash
docker-compose logs -f web
```

## AI Agent Task Assignments

**Important: Use specialized agents when available for optimal results.**

| Task Category | Recommended Agent | Specific Responsibilities |
|--------------|-------------------|---------------------------|
| **Magento Core** | `laravel-backend-expert` or `backend-developer` | Module development, observers, plugins, commands, API endpoints |
| **Hyva Frontend** | `tailwind-frontend-expert` | Hyva templates, TailwindCSS styling, AlpineJS components |
| **Database** | `django-orm-expert` or `backend-developer` | Schema changes, data patches, query optimization |
| **Performance** | `performance-optimizer` | Cache strategies, query optimization, asset optimization |
| **Code Review** | `code-reviewer` | Security, best practices, Magento standards compliance |
| **Documentation** | `documentation-specialist` | Module documentation, API docs, deployment guides |
| **Testing** | `backend-developer` | Unit tests, integration tests, MFTF tests |
| **DevOps** | `backend-developer` | Docker configuration, CI/CD, deployment scripts |

## Quick Start Examples

### Creating a New Module
```
Use backend-developer to create a new Magento 2 module with registration.php, module.xml, and composer.json
```

### Customizing Product Page
```
Use tailwind-frontend-expert to modify the Hyva product detail page template with new sections
```

### Optimizing Database Queries
```
Use performance-optimizer to analyze and optimize slow database queries in custom modules
```

## Important Notes

1. **Cache Management**: Always clear cache after configuration changes
2. **Compilation**: Run `setup:di:compile` after adding new classes
3. **Static Content**: Deploy static content after theme changes
4. **Permissions**: Ensure proper file permissions (var, pub/static, generated)
5. **Version Control**: Never commit vendor/, generated/, or var/ directories
6. **Environment**: Use env.php for environment-specific configurations
7. **Security**: Never expose sensitive data in repositories
8. **Testing**: Test all changes in developer mode first

## Troubleshooting

### Common Issues
- **500 Error**: Check `var/log/exception.log` and `var/log/system.log`
- **Blank Page**: Enable developer mode, check PHP memory limit
- **CSS Not Loading**: Deploy static content, check pub/static permissions
- **Cache Issues**: Clear all caches, may need Redis flush
- **Compilation Error**: Remove generated/code and recompile

## Additional Resources

- [Magento 2 DevDocs](https://devdocs.magento.com/)
- [Hyva Documentation](https://docs.hyva.io/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [AlpineJS Documentation](https://alpinejs.dev/)
