# 🏁 Advanced Routing

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
Route::get('/user', fn() => print("Hello World"), ['middleware1']);
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
