# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a PHP-based marketing website for 3PRIME Managed Hosting. It uses Bootstrap 5 for the frontend with pre-bundled assets. PHP is used only for server-side includes (header/nav), not database operations.

## Running Locally

```bash
# From the site/ directory
php -S localhost:8000
```

No build process is required - assets are pre-bundled and served directly.

## Deployment

The site deploys automatically via CircleCI when changes are pushed to the `main` branch:
- FTP mirrors changed files to `staging.ctwebdevelopment.com`
- Only modified files are uploaded (uses `--only-newer` flag)
- FTP credentials are stored in CircleCI environment variables (FTP_USER, FTP_PASS, FTP_HOST)

## Architecture

### Directory Structure
- `index.php` - Main landing page
- `assets/css/` - Pre-bundled stylesheets (`libs.bundle.css`, `theme.bundle.css`)
- `assets/js/` - Pre-bundled JavaScript (`vendor.bundle.js`, `theme.bundle.js`)
- `assets/img/` - Images and branding
- `assets/fonts/` - HK Grotesk Pro font and Feather icons
- `includes/` - PHP includes for `head.php` and `nav.php`

### Frontend Stack
- **Bootstrap 5** - Grid system, components, utility classes
- **Pre-bundled JS libraries**: AOS (scroll animations), BigPicture (lightbox), Smooth Scroll, Typed.js, CountUp.js, Jarallax (parallax)

### PHP Includes Pattern
Pages use PHP includes for shared components:
```php
<?php include 'includes/head.php'; ?>
<?php include 'includes/nav.php'; ?>
```

## Key Files

- `.circleci/config.yml` - CI/CD deployment configuration
- `index.php` - Primary entry point
- `includes/head.php` - Document head and meta tags
- `includes/nav.php` - Navigation menu
