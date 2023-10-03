# Basic Routing

## :tophat: Basic Request Routing

To define a basic route, here are the HTTP verb you can use with `route` class (e.g., GET, POST, PUT, DELETE).

The listed methods above takes two to three arguments:

* `uri`: the URI to match with request uri.
* `handler`: this parameter takes either a closure, template name or controller action that should be executed when the route is accessed.
* `middleware`: this is the code that runs before the main application loads.

### `Get` Method

This route method is used for getting form data or http post requests, this method takes three arguments.

The code snippet below explains how `get` route method can be used with Closure handler:

```php
Route::get('/', function () {
   return out('Hello world'); // return 'Hello world'
});
```

Or you can shorten the process by using the short closure handler:

```php
Route::get('/', fn () => out('Hello World'));
```

### &#x20;`Post` Method

This route method is used for getting form data or http post requests, this method takes three arguments:

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure** |object|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::post('/add-user', function() {
  $name = request()->post('user.name');
  return out($name);
});
```



### &#x20;`PUT` Method

This route method is used for making http put requests, this method takes three arguments:

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::post('/edit-user', function() {
  //...
});
```



### `DELETE` Method

This route method is used for making http delete requests, this method takes three arguments:

* [ ] `uri` : _string._
* [ ] `handler`:  **Closure**|_string._
* [ ] `middleware`: _string_|_array_.

#### :computer: Code Snippet:

```php
Route::delete('/user/delete/{id}', function(int $id) {
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

> the above code snippet automatically display or map the created template: `index.tpl` on '/' request uri

