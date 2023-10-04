# 🌠 Basic Routing

In order to define a basic route, here are the HTTP verb you can use with `route` class:

* GET
* POST
* PUT
* DELETE.

The listed methods above takes two to three arguments/parameters:

* `uri`: the URI to match with request uri.
* `handler`: this parameter takes either a closure, template name or controller action that should be executed when the route is accessed.
* `middleware`: this is the code that runs before the main application loads.



### `GET` Method

This route method is used for getting form data or http post requests, this method takes three arguments.

```php
Route::get($uri, $handler, $middleware);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

The code snippet below explains how `get` route method can be used with Closure handler:

```php
Route::get('/', function () {
   return out('Hello world'); // return 'Hello world'
});
```

Or you can shorten the process by using the short closure handler:

```php
Route::get('/', fn() => out('Hello World'));
```



### &#x20;`POST` Method

This route method is used for getting form data or http post requests, this method takes three arguments:

```php
Route::post($uri, $handler, $middleware);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::post('/add-user', function() {
  // ...
});
```



### &#x20;`PUT` Method

This route method is used for making http put requests, this method takes three arguments:

```php
Route::put($uri, $handler, $middleware);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::put('/edit-user', function() {
  // ...
});
```



### `DELETE` Method

This route method is used for making http delete requests, this method takes three arguments:

```php
Route::delete($uri, $handler, $middleware);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::delete('/user/delete/{id}', function(int $id) {
  // ...
});
```

### `MIXED` Method

This route method is used for handling custom specified request methods, this method takes four arguments:

```php
Route::mixed($methods, $uri, $handler, $middleware);
```

* [ ] `methods`: _array_
* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::mixed(['GET', 'POST'], '/user/profile/edit', function() {
  //...
});
```



### `ANY` Method

This route method is used to handle all request methods, this method takes three arguments:

```php
Route::any($uri, $handler, $middleware);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::any('/static-page', function() {
  //...
});
```



### Static Page Rendering

`Get` route method can also be used to display a static page or template located at the `views/` folder in the application main directory:

> Note: Fastvolt make use of Smarty as it's default templating system.

Assuming we created a new `index.tpl` template file in the `views/` folder, then the template can be directly displayed using the `route` method:

```php
Route::get('/', 'index');
```

> the above code snippet automatically display or map the created template: `index.tpl` on '/' request uri.



### Route Parameters

In Fastvolt, you can define route parameters by enclosing them in curly braces `{id}` or using colon `:id`, These parameters capture values from the URL and pass them to your route handler as variables.

**URL Snippet:**

```batch
# considering this url
http:://www.myblog.net/blog/13
```

**Code Representation:**&#x20;

```php
Route::get('/blog/{id}', function(int $id) {
    return out("you are viewing blog id: {$id}");
});
```

The above code snippet captures the {id} value from the url snippet, then converts the {id} value to variable, the output of the above code while accessing the url: `http:://www.myblog.net/blog/13` from the browser will be:

```sh
you are viewing blog id: 13
```



### Route Groups

Route groups allow you to apply common attributes, such as middleware to a set of routes.

&#x20;Route grouping is useful when you want to group your routes into sections and the `route` method takes one parameter:

```php
Route::group($prefix);
```

`prefix`: _string_.



:computer: **Logic Representation:**&#x20;

```php
$route = Route::group('/user');

  # uri: '/user/dashboard'
  $route->get('/dashboard', function() {
         return out('This is the main user dashboard!');
  });
    
  # uri: '/user/profile'
  $route->get('/profile', function() {
         return out('This is the user profile!');
    });
```
