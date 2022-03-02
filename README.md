# Laravel Fortify for Filament Admin

[![Latest Version on Packagist](https://img.shields.io/packagist/v/wychoong/filament-fortify.svg?style=flat-square)](https://packagist.org/packages/wychoong/filament-fortify)
[![GitHub Tests Action Status](https://img.shields.io/github/workflow/status/wychoong/filament-fortify/run-tests?label=tests)](https://github.com/wychoong/filament-fortify/actions?query=workflow%3Arun-tests+branch%3Amain)
[![GitHub Code Style Action Status](https://img.shields.io/github/workflow/status/wychoong/filament-fortify/Check%20&%20fix%20styling?label=code%20style)](https://github.com/wychoong/filament-fortify/actions?query=workflow%3A"Check+%26+fix+styling"+branch%3Amain)
[![Total Downloads](https://img.shields.io/packagist/dt/wychoong/filament-fortify.svg?style=flat-square)](https://packagist.org/packages/wychoong/filament-fortify)

This package provides the UI for using Fortify in Filament Admin Panel

## Installation

You can install the package via composer:

```bash
composer require wychoong/filament-fortify
```

You can intallation command and run the migrations with:

```bash
php artisan filament-fortify:install 
php artisan migrate
```
The installation command does few things to speed up the installation process:
```
- Publish Fortify files
- Publish Fortify migration
- Add FortifyServiceProvider to config/app.php
```

**As this package is only providing UI for Fortify, kindly refer [Laravel Fortify](https://laravel.com/docs/9.x/fortify) documentation to setup, eg: User model.** 

## Optional

You can publish filament-fortify config file with:

```bash
php artisan vendor:publish --tag="filament-fortify-config"
```

Optionally, you can publish the views using

```bash
php artisan vendor:publish --tag="filament-fortify-views"
```

## Usage

This package respect the features configured in config/fortify.php, refer [Laravel Fortify](https://laravel.com/docs/9.x/fortify) to enable/disable features.

To make the installation seemless, the following configs are overrided in the package.
```php
config([
    ## override filament login page
    'filament.auth.pages.login' => Auth\Login::class,
    ## force fortify view enabled
    'fortify.views' => true,
    ## force fortify to use filament home_url
    'fortify.home' => config('filament.home_url'),
]);
```

#### 2FA Page
A simple enable/disable user's 2fa page is included. 

You can change the page's title, navigation group, navigation label in service provider:

```php
use WyChoong\FilamentFortify\Facades\FilamentFortify;

public function boot()
{
    FilamentFortify::navigationGroup(__('your-nav-group'));
    FilamentFortify::navigationLabel(__('your-nav-label'));
    FilamentFortify::pageTitle(__('your-page-title'));
}
```

To disable it, publish the config file and set:
```php
    'register-page' => false,
```

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [wychoong](https://github.com/wychoong)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.