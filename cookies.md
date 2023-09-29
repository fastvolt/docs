# Cookies

A Cookie in Foster Framework is a small piece of data that is sent from a web server to a user's web browser and stored on the user's device. Cookies are commonly used to store information about the user's interaction with a website, such as preferences, session data, and tracking information. 
They allow websites to remember users between different requests and sessions.

## Usage
Cookie can be managed using the cookie standalone helper object, here is quick sample of how it works below.

**Import The `Cookie` Helper Package**: 
<br>
```php
use FastVolt\Helper\Cookie;
```
**Then access it amazing features** 🙂
```php
use FastVolt\Helper\Cookie;

// store cookie
Cookie::store('username', 'vincent'); // return true

// get stored cookie
Cookie::get('username'); // return 'vincent'

// update stored cookie
Cookie::store('username', 'foster');

// get updated cookie
Cookie::get('username'); // return 'foster'

// delete stored cookie
Cookie::delete('username'); // return true
```
 <br>

## Cookie Methods

 ### Store
 Cookie can be store and updated in this format:
 
 ```php
Cookie::store('username', 'vincent'); // return bool
```
The `store` method takes only three parameters
 - `handle`: string
 - `message`: string|array
 - `expires`: int (***optional***).

<br>

### Stable
Here is another approach similar to `store` method to store cookie that never expires using the `stable` method:

 ```php
Cookie::stable('username', 'vincent'); // return bool
```
The `stable` method takes only three parameters
 - `handle`: string
 - `message`: string|array
 - `expires`: int (***optional***).

> **NOTE**: `stable` method should not be used to store importance informations for security reasons.

<br>

### Retrieve
Stored Cookie can be retrieved using this method:

 ```php
Cookie::get('username');  // return string|int
```
The `get` method takes only one parameter
 - `cookie_name`: string

<br>

### Delete
Delete stored cookie
```php
Cookie::delete('username'); // return bool
```
The `delete` method takes only one parameter
 - `cookie_name`: string

<br>

### Has
This method is been used to check if cookie exist

```php
Cookie::has('username'); // return bool
```
**Real Code Usage**:
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
 - `cookie_name`: string
