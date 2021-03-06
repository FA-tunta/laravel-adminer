# Laravel Adminer Database Manager

Light weight [Adminer](https://www.adminer.org) database management tool integrated into Laravel 5/6/7/8.

Various database support: MySQL, SQLite, PostgreSQL, Oracle, MS SQL, Firebird, SimpleDB, MongoDB, Elasticsearch, and etc.

> v5.0 New Feature: 
> - enable autologin to database (default: `false`)
> - customize route prefix (default: `adminer`)

## Installation

```
composer require onecentlin/laravel-adminer
```

OR

Update `composer.json` in require section:

```json
"require": {
    "onecentlin/laravel-adminer": "^5.0"
},
```

Run:
```
composer update
```

## Prerequisite

Update `config/app.php`

```php
'providers' => [
    ...
    Onecentlin\Adminer\ServiceProvider::class,
];
```

## Publish config and theme file

```
php artisan vendor:publish --provider="Onecentlin\Adminer\ServiceProvider"
```

This action will copy two files:

- `config/adminer.php` - Adminer config file
- `public/adminer.css` - Adminer theme file

### config file: `config/adminer.php`

If you only want to config autologin feature, you may just add below content to `config/adminer.php` file.

```php
<?php

return [
    'autologin' => false,
    'route_prefix' => 'adminer',
    'middleware' => ['web'],
]
```

> <span style="color: #a00">ATTENSION: Please only enable autologin with authenticated protection.</span>

### theme file: `public/adminer.css`

You may download `adminer.css` from [Adminer](https://www.adminer.org) or create custom style, and place it into `public` folder.

## Access adminer

Open URL in web browser

```
http://[your.domain.com]/adminer
```

![Screenshot](https://raw.githubusercontent.com/onecentlin/laravel-adminer/master/screenshots/adminer-db-support.png "various database support")

## Remarks

Due to function name conflicts of Laravel 5 and Adminer, adminer.php file
functions `cookie()`, `redirect()` and `view()` are prefixed with `adm_` prefix.

Inspired by [miroc](https://github.com/miroc/Laravel-Adminer)
