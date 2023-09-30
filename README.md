# 👋 Introduction

FastVolt is a simple, fast and scalable MVC (Model View Controller) php web framework used for building web applications. this framework is best suited for entry-level php developers because of it simplicity. our framework is your ideal companion for creating powerful, modern, and scalable web applications.

***

In order to get a guide on this framework installation, see...

{% content-ref url="overview/installation.md" %}
[installation.md](overview/installation.md)
{% endcontent-ref %}

***

### "Hello World" Comparison

{% tabs %}
{% tab title="FastVolt" %}
```php
<?php

use FastVolt\Router\Route;

Route::get('/home', function() {
   return out('Hello, World');
});

```
{% endtab %}

{% tab title="Slim Framework" %}
```php
<?php
use Psr\Http\Message\ResponseInterface as Response;
use Psr\Http\Message\ServerRequestInterface as Request;
use Slim\Factory\AppFactory;

require __DIR__ . '/../vendor/autoload.php';

$app = AppFactory::create();

$app->get('/home', function (Request $request, Response $response, $args) {
    $response->getBody()->write("Hello world!");
    return $response;
});

$app->run();
```
{% endtab %}

{% tab title="Laravel" %}
```php
<?php

use Illuminate\Support\Facades\Route;
 
Route::get('/home', function () {
    return 'Hello World';
});
```
{% endtab %}
{% endtabs %}

***

# Features
PHP has alot of frameworks you choose from, but what exactly made Foster framework more better than them?
- [x] Simple Installation
- [x] Low Learning Curve
- [x] Built-in Simple Http Router
- [x] Middleware
- [x] Max Security
- [x] MVC Architecture
- [x] Less Development Time
- [x] Developer Tool (Automatic Code Generation)
- [x] Templating Engine (Smarty).

