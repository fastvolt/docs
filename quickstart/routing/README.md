# 🎌 Routing

## Initialization

```php
use FastVolt/Router/Route;
```

> Note that Routing in FastVolt take place in `routes/main.route.php`

<br>
In this documentation, you'll learn how to define, configure, and leverage the routing system in FastVolt Framework to handle incoming requests and build robust web applications.

<br>

Before diving into routing, ensure that FastVolt Framework is properly installed and configured in your project, refer to the installation documentation for detailed instructions.
<br>

## Basic Routing
To define a basic route, here are the HTTP verb you can use with `route` class (e.g., GET, POST, PUT, DELETE). 

The listed methods above takes two to three arguments: 

- `uri`: the URI to match with request uri.
- `handler`: this parameter takes either a closure, template name or controller action that should be executed when the route is accessed.
- `middleware`: this is the code that runs before the main application loads.


### `Get` Method

The code snippet below explains how `get` route method is been used with Closure handler:

```php
Route::get('/', function () {
   return out('Hello world'); // return 'Hello world'
});
```
Or you can shorten the process by using the short closure:

```php
Route::get('/', fn () => out('Hello World'));
```

### Static Page Rendering


`Get` route method can also be used to display a static page or template located at the `views/` folder in the application main directory:

>  Note: FastVolt make use of Smarty as it's default templating system.


 Assuming we created a new `index.tpl` template file in the `views/` folder, then the template can be directly displayed using the `route` method:

 ```php
Route::get('/', 'index');
```
 > the above code snippet automatically display or map the created template: `index.tpl` on '/' request uri



