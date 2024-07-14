# 🏁 Basic Routing

In order to initialize router package, visit:

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}


To define a basic route, here are the HTTP verbs/methods you can use in the `Router` package:

* GET
* POST
* PUT
* DELETE.

The above listed methods takes two to four arguments/parameters:

* `uri`: the URI to match with request uri.
* `handler`: this parameter takes either a closure, template name or controller action that should be executed when the route is accessed.
* `middleware`: this is the code that runs before the main application loads.
* `name`: this is an alias name for the defined route, it it used with `route` function to get a specific route info. 



### `GET` Method

This route method is used for getting http get requests, this method takes three arguments.

```php
Route::get($uri, $handler, $middleware, $name);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_|_null_.
* [ ] `name`: _string_|_null_.

#### :computer: Code Snippet:

```php
Route::get('/homepage', function() {
  // ...
}, name: 'home');
```



### &#x20;`POST` Method

This route method is used for getting form data or http post requests, this method takes three arguments:

```php
Route::post($uri, $handler, $middleware, $name);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_|_null_.
* [ ] `name`: _string_|_null_.

#### :computer: Code Snippet:

```php
Route::post('/add-user', function() {
  // ...
}, name: 'add_new_user');
```



### &#x20;`PUT` Method

This route method is used for making http put requests, this method takes three arguments:

```php
Route::put($uri, $handler, $middleware);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_|_null_.
* [ ] `name`: _string_|_null_.

#### :computer: Code Snippet:

```php
Route::put('/edit-user', function() {
  // ...
}, name: 'edit_user');
```



### `DELETE` Method

This route method is used for making http delete requests, this method takes three arguments:

```php
Route::delete($uri, $handler, $middleware, $name);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_|_null_.
* [ ] `name`: _string_|_null_.

#### :computer: Code Snippet:

```php
Route::delete('/user/delete', function() {
  // ...
}, name: 'delete_user');
```

### `MIXED` Method

This route method is used for handling custom specified request methods, this method takes four arguments:

```php
Route::mixed($methods, $uri, $handler, $middleware, $name);
```

* [ ] `methods`: _array._
* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_|_null_.
* [ ] `name`: _string_|_null_.

#### :computer: Code Snippet:

```php
Route::mixed(['GET', 'POST'], '/settings, function() {
  //...
}, name: 'settings');
```



### `ANY` Method

This route method is used to handle all request methods, this method takes three arguments:

```php
Route::any($uri, $handler, $middleware, $name);
```

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_array_|_string._
* [ ] `middleware`: _string_|_array_|_null_.
* [ ] `name`: _string_|_null_.

#### :computer: Code Snippet:

```php
Route::any('/homepage', function() {
  //...
}, name: 'home);
```



### Controller Route Handler

The code snippet below explains how `get` route method can be used with an object as handler:

<pre class="language-php"><code class="lang-php"><strong>use App\Http\Controller\UserController;
</strong><strong>
</strong><strong>Route::get('/', [UserController::class, 'index']);
</strong></code></pre>

Or you can shorten the process by denoting the controller as string:

```php
Route::get('/', 'UserController@index');
```

> In the above code snippet, **`index()`** method is fetched from **`UserController`** class and executed/mapped on `/` request uri.



### Static Page Rendering

`Get` route method can also be used to display a static page or template located at the `views/` folder in the application root directory:

> Note: You can use Smarty template, PHP file or HTML file as the route handler, it will be automatically fetched from views directory and rendered.
> Also note that you can format the handler name as `index` instead of `index.html` and when using this method, fastvolt automatically fetch the first file it encounters, so if `index.html` comes before `index.tpl`, `index.html` will be rendered.

#### :computer: Code Snippet:
```php
// short version
Route::get('/', 'index', name: 'home');

// full version
Route::get('/', 'index.tpl', name: 'home');
```

> the above code snippet automatically display or map the created template: `index.tpl` on '/' request uri.

