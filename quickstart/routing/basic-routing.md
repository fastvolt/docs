# 🏁 Basic Routing

In order to initialize router package, visit:

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}

To define a basic route, here are the HTTP verb you can use with `route` class:

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

> In the code above, **`index()`** method in **`UserController`** class is executed on `/` request uri.



### Static Page Rendering

`Get` route method can also be used to display a static page or template located at the `views/` folder in the application main directory:

> Note: Fastvolt make use of Smarty as it's default templating system.

Assuming we created a new `index.tpl` template file in the `views/` folder, then the template can be directly displayed using the `route` method:

```php
Route::get('/', 'index');
```

> the above code snippet automatically display or map the created template: `index.tpl` on '/' request uri.



