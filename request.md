# ⤴ Request

## Initialization

```php
use FastVolt\Core\Http\HttpRequest as Request;
```
or you can use the functional method to initialise the `HttpRequest` class:

```php
request();
```

## Quick Usage
```php
# class initialisation method
$request = new Request();
$request->phpversion(); // 8.1

# functional method
request()->phpversion(); // 8.1
```

The request class object provides an easy way to access various types of incoming HTTP requests. It allows you to retrieve input data, query parameters, headers, uploaded files, and more.

The request object comes with some methods that extends its functionalities, here are the full list of methods available in FastVolt Framework `Request` object.


### 📦 GET METHOD

The `GET` request method is used for getting/retrieving query data in a request body using the `get` and `getQuery` method.

> However, `hasQuery` method can be used to check if the request data exist or not.

Let's take for example, a full url looks like this:

```sh
https://myblog.net/blog/?id=1&comment=8
```

To get `id` data, which is `1` , here is a way to get it using the `get` method:

```php
// using "get" method
$request->get('id'); // return 1
```

To get both `id` and `comment` data, `getQuery` allows getting two or more data in **GET** request header:

```php
$request->getQuery(['id', 'comment']); // return array[1, 8]
```

Also note that the `getQuery` and `get` method has a second and third parameter, which is the `$fallback` and `$escape_output`, this parameters has a default value of null and true respectively.

> `$fallback`: this parameter is like a backup way to ensure the `get` method parameter doesn't return null, it automatically return it's value when the query parameter is null or empty.

> `$escape_output` automatically sanitize the `getQuery` or `get` method output.

The main difference between `get` and `getQuery` is that `get` method can only accept one parameter while `getQuery` method can take multiple parameters.



### 📦 POST METHOD

The `POST` request method is used for retrieving post request data in a request body using the `post` and `postItems` method.

> However, `hasPostItems` method can be used to check if the request data exist or not.

Unlike `get` method, `post` method is mostly used for retrieving form data in a web application.

Here is a quick example on how `post` request method works in Foster Framework development.

Consider this web form in html:

```html
<form action="POST">
{csrf_token}
<input type="text" name="user_name" placeholder="Input Full Name"/>
<input type="submit">
</form>
```

Imagine we submitted the form data with "Oladoyinbo Vincent" as the Full Name, we can retrieve and use the sent form data using this method:

```php
# using "post" method
request()->post('user_name'); // return "Oladoyinbo Vincent"

# using "postItems" method
request()->postItems(['user_name']); // return array(0 => 'Oladoyinbo Vincent')
```

> `postItems` method can also be used, if there are multiple input fields to get from the form.




### 📦 FILES

The `Files` request method is used for retrieving partially uploaded files in a request body by using the `file` and `getFiles` method.

> `hasFile` method can be used to check if the request data exist or not.

Here is a simple example of how `file` and `getFiles` can be used to retrieve temporary uploaded files in request body.

```php
// get single request file 
request()->file('file1'); // return single array([...])

// get multiple request files
request()->getFiles(['file1', 'file2']); // return multiple array([[...], [...]])
```



### 📦 COOKIES

Cookies are commonly used to store information about the user's interaction with a website, such as preferences, session data, and tracking information. They allow websites to remember users between different requests and sessions. below information explains how cookies work in FastVolt Framework:

```php
request()->setCookie('user_name', 'vincent'); // true

request()->getCookie('user_name'); // vincent
```


**Setting and Modifying a Cookie:**

You can set a cookie in PHP using the `setCookie` method. This method takes only four core parameters, including the name, value, minutes, samesite.

> Use `isCookie` or `hasCookie` method to check if Cookie exist before retrieval

```php
$request->setCookie('user_name', 'vincent'); // return bool
```

* `name`: your preferred cookie name
* `value`: input the data you are storing, only `string` and `int` value type are accepted.
* `minutes` **(optional**): the cookie exipiry date, default value for this parameter is "1 day".
* `samesite` **(optional**): cookie level of security, _**Options**_: `None` || `Lax (Default)` || `Strict`.



**Retrieving Cookie Values:**

Once a cookie is set, it can be accessed in subsequent requests using the `getCookie` method.

```php
$request->getCookie('user_name'); // return "vincent"
```



**Deleting Cookies:**

You can delete cookies by using the `deleteCookie()` method with the cookie name you set.

```php
$request->deleteCookie('username'); return bool
```

> Cookies are stored on the user's device, and while they are a convenient way to store small amounts of data, they have security considerations. Sensitive information should not be stored in cookies because they can be accessed and modified by users.



### Retrieve All Request Body

In some case during development, there might be the need of getting all request body in key and value format. Here is a simple method to get it using the `fetch_all_request_data` method in request object.

```php
$request->fetch_all_request_data(); // returns array([...])
```


## Functions

1. `root_dir()`: returns root directory.
2. `foster_app_dir()`: returns app directory url.
3. `foster_database_dir()`: returns database directory url.
4. `foster_dir_path()`: returns specified directory path and takes in a parameter (e.g views, models).
5. `escape()`: returns escaped/sanitized output result.
6. `strip_text()`: returns html/slash stripped string output.
7. `is_email()`: check if email is valid, this returns bool.
8. `is_json()`: check if json is valid, this returns bool.
9. `get_status_code_message()`: returns status code name string representation.
10. `verify_csrf_token()`: this is used for verifying and validating form csrf tokens, this returns bool.
11. `csrf_error()`: this returns csrf error message, default message is: "Invalid Request, Please Reload Page".
12. `out()`: this is used instead of php echo keyword to invade security issues.
13. `response()`: this performs same function as out() method.
14. `redirect()`: this extends and return Redirect Response method, used for http header redirect.
15. `error_message()`: this returns error message with http response code, also similar to out() and response().
16. `is_audio()`: the function checks if file is audio.
17. `is_image()`: the function checks if file is image.
18. `is_video()`: the function checks if file is video
19. `is_archive()`: the function checks if file is audio.
20. `is_document()`: the function checks if file is document
