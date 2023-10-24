# 🏁 Advanced Routing

In order to initialize router package, visit:

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}

### Route Parameters

In Fastvolt, you can define route parameters by enclosing them in curly braces `{id}` or using colon `:id`, These parameters capture values from the URL and pass them to your route handler as variables.

#### URL Snippet

consider this url for example:

```batch
http:://www.myblog.net/blog/13
```

#### Logic Representation:&#x20;

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



#### **Code Representation**

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
Route::get('/user', function() {

   // ...
 
}, ['middleware1']);
```

Or:

```php
Route::middleware(['middleware1'])->get('/', function() {
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



### Namespace Routes

Namespace route is useful only when you have your controller files in another directory except from the main controller directory `App\Http\Controller`, then you can specify the exact directory namespace in this format:

For example, if we created a new folder `app/Http/Controller/Auth` which has a namespace of `App\Http\Controller\Auth` , and also created a new `UserController.php` file which contains the following code:

```php
<?php

namespace App\Http\Controller\Auth;

use FastVolt\Core\Controller;

class UserController extends Controller {

  public function index(){
    // ...
  }
  
  public function login(){
    // ...
  }
  
  public function register(){
    // ...
  }

}
```

We can implement request routing to access this controller and it's methods using the below code format:

```php
$auth = Route::namespace('App\Http\Controller\Auth');

   // returns 'index' method
   $auth->get('/' 'UserController@index');
   
   // returns 'login' method
   $auth->get('/login' 'UserController@login');
   
   // returns 'register' method
   $auth->get('/register' 'UserController@register');

```



