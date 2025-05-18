# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Rememberall is a Ruby on Rails 7.2.2 application configured as a Progressive Web Application (PWA). It uses PostgreSQL as the database, Tailwind CSS for styling, and Hotwire (Turbo and Stimulus) for JavaScript functionality.

## Timeline Considerations
- When suggesting timelines for implementation tasks, use hours or minutes instead of days
- Consider that we're working with advanced AI systems (Claude, 2025 version) that can dramatically accelerate development
- Feature implementations that might traditionally take days can now be completed in hours or even minutes

## Git Workflow
- Never commit on the main branch, switch to a new branch if not already on one
- When committing changes, think whether a new commit is necessary or amending the last one would do

## Code Style Guidelines
- **Rails Patterns**: Follow "fat models, skinny controllers" approach
- **Line Length**: Keep to 80 characters or less
- **Method Chaining**: Chain methods on a new line after indenting with 2 spaces
- **DRY**: Use concerns for shared functionality
- **Naming**: Use meaningful method/variable names to minimize comments
- **DB Performance**: Use includes/preload/eager_load to avoid N+1 queries

## Development Setup

### Setup Commands

```bash
# Initial setup
bin/setup  # Installs dependencies and prepares database

# Start development server
bin/dev    # Runs Rails server and Tailwind CSS watcher using Foreman on port 3000
```

### Database Commands

```bash
# Create or migrate database
bin/rails db:prepare

# Reset database
bin/rails db:reset

# Prepare test database
bin/rails db:test:prepare
```

## Testing

```bash
# Run all tests
bin/rails test

# Run system tests
bin/rails test:system

# Run a specific test file
bin/rails test test/path/to/file_test.rb

# Run a specific test (line number specified)
bin/rails test test/path/to/file_test.rb:42
```

## Linting and Security

```bash
# Run Ruby linting
bin/rubocop

# Run security scan
bin/brakeman

# Audit JavaScript dependencies
bin/importmap audit
```

## Architecture

- Standard Rails MVC architecture
- PostgreSQL database
- PWA configuration with service worker and manifest
- Tailwind CSS for styling
- Hotwire (Turbo and Stimulus) for dynamic frontend interactions
- Importmaps for JavaScript module management

### Key Files/Directories

- `app/views/pwa/` - PWA manifest and service worker templates
- `app/assets/tailwind/` - Tailwind CSS configuration
- `app/javascript/controllers/` - Stimulus controllers
- `config/routes.rb` - Application routes including PWA and health check endpoints
- `Procfile.dev` - Development process configuration for Foreman

## CI/CD

The project uses GitHub Actions for continuous integration with the following steps:
- Security scanning with Brakeman for Ruby code
- Security scanning for JavaScript dependencies
- Code linting with Rubocop
- Running tests with a PostgreSQL service container