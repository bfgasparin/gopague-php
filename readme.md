# Go Pague PHP Library

## Requirements

PHP 7.0.1 and later.

## Composer

You can install the bindings via [Composer](http://getcomposer.org/). Run the following command:

```bash
composer require go-pague/go-pague-php
```

To use the go pague classes, use Composer's [autoload](https://getcomposer.org/doc/00-intro.md#autoloading):

```php
require_once('vendor/autoload.php');
```

## Dependencies

This library require the following extension in order to work properly:

- [`curl`](https://secure.php.net/manual/en/book.curl.php), although you can use your own non-cURL client if you prefer
- [`json`](https://secure.php.net/manual/en/book.json.php)
- [`mbstring`](https://secure.php.net/manual/en/book.mbstring.php) (Multibyte String)

If you use Composer, these dependencies should be handled automatically. If you install manually, you'll want to make sure that these extensions are available.

## Getting Started

First you need set the email and password of the user to login to Go Pague API.

```php
GoPague\GoPague::setEmail('myemail@foo.bar')
GoPague\GoPague::setPassword('secret');
```

Now you can use the resource binding classes to interact with Go Pague API.

```php
// gets the list of banks
$banks = GoPague\Bank::all();
```

> **Note**: See `Resource Binding Classes` section to know all classes and methods available.

The binding classes will automatically use the previous given email and password to login
and autenticate to the API before the first API request.

But if you want to autenticate to API manually, just use:

```php
$credentials = GoPague\GoPague::login('myemail@foo', 'secret');

// gets the list of banks
$banks = GoPague\Bank::all();
// ...
```

You can access the Logged User data any time just calling the method:

```php
$credencials = GoPague::credentials();

echo $credentials->token;   // the Authenticated Token
echo $credentials->userId;   // the Authenticted User Id
echo $credentials->clientIds;   // The client ids linked to the Authenticted User
```

## Resource Binding Classes

@todo

## Development

Install dependencies:

``` bash
composer install
```

## Tests

Install dependencies as mentioned above (which will resolve [PHPUnit](http://packagist.org/packages/phpunit/phpunit)), then you can run the test suite:

```bash
./vendor/bin/phpunit
```

Or to run an individual test file:

```bash
./vendor/bin/phpunit tests/SomeTest.php
```

