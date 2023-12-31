# 🍪 Cookies

## Initialization

```php
use FastVolt\Helper\Cookie;
```

### Quick Usage

```php
# init cookie helper class

use FastVolt\Helper\Cookie;

# store cookie
Cookie::store('user', 'vincent'); // true

# retrieve cookie
Cookie::get('user'); // vincent

# delete cookie
Cookie::delete('user'); // true
```



A Cookie is a small piece of data that is sent from a web server to a user's web browser and stored on the user's device.

Cookies are commonly used to store information about the user's interaction with a website, such as preferences, session data, and tracking information. They allow websites to remember users between different requests and sessions.



## Cookie Methods

### 📦 Store

Cookie can be store and updated in this format:

```php
Cookie::store('username', 'vincent'); // return bool
```

The `store` method takes only three parameters

* `handle`: string
* `message`: string|array
* `expires`: int (_**optional**_).



### 📦 Stable

Here is another approach similar to `store` method to store cookie that never expires using the `stable` method:

```php
Cookie::stable('username', 'vincent'); // return bool
```

The `stable` method takes only three parameters

* `handle`: string
* `message`: string|array
* `expires`: int (_**optional**_).

> **NOTE**: `stable` method should not be used to store importance informations for security reasons.



### 📦 Retrieve

Stored Cookie can be retrieved using this method:

```php
Cookie::get('username');  // return string|int
```

The `get` method takes only one parameter

* `cookie_name`: string.



### 📦 Delete

Delete stored cookie

```php
Cookie::delete('username'); // return bool
```

The `delete` method takes only one parameter

* `cookie_name`: string



### 📦 Has

This method is been used to check if cookie exist

```php
Cookie::has('username'); // return bool
```

**Method Usage**:

```php
Route::get('/home', function(){
// store cookie
Cookie::store('username', 'vincent');

// check if cookie exist
if(Cookie::has('username')){
// get store cookie
   Cookie::get('username');
}
});
```

The `has` method takes only one parameter

* `cookie_name`: string
