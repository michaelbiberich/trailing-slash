# middlewares/trailing-slash

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Quality Score][ico-scrutinizer]][link-scrutinizer]
[![Total Downloads][ico-downloads]][link-downloads]
[![SensioLabs Insight][ico-sensiolabs]][link-sensiolabs]

Middleware to normalize the trailing slash of the uri path. By default removes the slash so, for example, `/post/23/` is converted to `/post/23`. Useful if you have problems with the router.

## Requirements

* PHP >= 5.6
* A [PSR-7](https://packagist.org/providers/psr/http-message-implementation) http mesage implementation ([Diactoros](https://github.com/zendframework/zend-diactoros), [Guzzle](https://github.com/guzzle/psr7), [Slim](https://github.com/slimphp/Slim), etc...)
* A [PSR-15](https://github.com/http-interop/http-middleware) middleware dispatcher ([Middleman](https://github.com/mindplay-dk/middleman), etc...)

## Installation

This package is installable and autoloadable via Composer as [middlewares/trailing-slash](https://packagist.org/packages/middlewares/trailing-slash).

```sh
composer require middlewares/trailing-slash
```

## Example

```php
$dispatcher = new Dispatcher([
	(new Middlewares\TrailingSlash(true))
		->redirect()
]);

$response = $dispatcher->dispatch(new Request());
```

## Options

#### `__construct(false)`

Set `true` to add the slash instead remove so, for example, `post/23` is converted to `/post/23/`. Note that if the path contains an extension, the slash is **NOT** added. For example, `images/image.png` remains the same, instead be converted to `images/image.png/`.

#### `redirect(true)`

Set this option to return a `301` response redirecting to the new path

---

Please see [CHANGELOG](CHANGELOG.md) for more information about recent changes and [CONTRIBUTING](CONTRIBUTING.md) for contributing details.

The MIT License (MIT). Please see [LICENSE](LICENSE) for more information.

[ico-version]: https://img.shields.io/packagist/v/middlewares/trailing-slash.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/middlewares/trailing-slash/master.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/g/middlewares/trailing-slash.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/middlewares/trailing-slash.svg?style=flat-square
[ico-sensiolabs]: https://img.shields.io/sensiolabs/i/36786f5a-2a15-4399-8817-8f24fcd8c0b4.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/middlewares/trailing-slash
[link-travis]: https://travis-ci.org/middlewares/trailing-slash
[link-scrutinizer]: https://scrutinizer-ci.com/g/middlewares/trailing-slash
[link-downloads]: https://packagist.org/packages/middlewares/trailing-slash
[link-sensiolabs]: https://insight.sensiolabs.com/projects/36786f5a-2a15-4399-8817-8f24fcd8c0b4
