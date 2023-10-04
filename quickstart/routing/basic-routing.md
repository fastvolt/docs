# 🏁 Basic Routing

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

This route method is used for getting http get requests, this method takes three arguments.

```php
Route::get($uri, $handler, $middleware);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::get('/homepage', function() {
  // ...
});
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
Route::delete('/user/delete', function() {
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



### Controller Route Handler

The code snippet below explains how `get` route method can be used with controller object as handler:

<pre class="language-php"><code class="lang-php"><strong>use App\Http\Controller\UserController;
</strong><strong>
</strong><strong>Route::get('/', [UserController::class, 'index']);
</strong></code></pre>

Or you can shorten the process by denoting the controller as string:

```php
Route::get('/', 'UserController@index');
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

**URL Snippet**

consider this url for example:

```batch
http:://www.myblog.net/blog/13
```

**Logic Representation:**&#x20;

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

Route grouping is useful when you want to group your routes into sections and the `route` group method takes two parameter:

```php
Route::group($prefix, $middleware);
```

* `prefix`: _string_.
* `middleware`: _array_|_string_.



:computer: **Code Representation:**&#x20;

```php
$route = Route::group('user');

  # uri: '/user/dashboard'
  $route->get('/dashboard', function() {
         return out('This is the main user dashboard!');
  });
    
  # uri: '/user/profile'
  $route->get('/profile', function() {
         return out('This is the user profile!');
    });
```



### Middleware

Middleware is a very simple and straight-forward way to filter HTTP requests entering your application. You can apply middleware to routes or route groups to perform tasks like authentication, authorization, and input validation.

Middleware can be assigned to single route in this format:

```php
Route::middleware(['verify.user'])->get('/', function() {
   // ..
});
```

Or you can apply middleware to route groups in this format:

<pre class="language-php"><code class="lang-php"><strong>$route = Route::group('user', ['middleware1', 'middleware2']);
</strong>   # index page 
   $route->get('/', function() {
      // ...
   });
   
   # blog page
   $route->get('/blog', function() {
      // ...
   });
</code></pre>

> The '**middleware1**', '**middleware2**' will automatically be applied to all sub-routes in the example above.&#x20;

