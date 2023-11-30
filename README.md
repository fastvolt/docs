---
cover: .gitbook/assets/fastvolt.png
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: true
---

# 👋 Introduction

Fastvolt is a simple, fast and minimal MVC (Model View Controller) PHP web framework, used for building web applications and APIs. this framework is best suited for entry-level PHP developers because of it simplicity. Our framework is your ideal companion for creating powerful, modern, and minimal web applications.

### "Hello World" Comparison

#### ⚡ Fastvolt:

```php
<?php

use FastVolt\Router\Route;

Route::get('/home', function() {
   return out('Hello, World');
});

```

#### 🌀 Slim Framework:

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

#### 📦 Laravel:

```php
<?php

use Illuminate\Support\Facades\Route;
 
Route::get('/home', function () {
    return 'Hello World';
});
```

### 🌟 Features

PHP has alot of frameworks you can choose from, but what exactly made FastVolt framework more better than them?

* [x] Simple Installation
* [x] Low Learning Curve
* [x] Built-in Simple Http Router
* [x] Middleware
* [x] Max Security
* [x] MVC Architecture
* [x] Less Development Time
* [x] Developer Tool (Automatic Code Generation)
* [x] Support Various Templating Engines (Smarty, PHP).
