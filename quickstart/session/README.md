# ⭐ Session

## Initialization

```php
use FastVolt\Helper\Session
```

### Usage

```php
Session::store('user', 'vincent');
```





In Foster Framework, the PHP session handling mechanism allows you to store and manage user-specific data across multiple requests and sessions. Sessions are a way to maintain stateful information about a user's interactions with a web application. Foster Framework provides a convenient and secure way to work with sessions using its built-in session management features.

Here's how sessions work in Foster Framework:

## Starting a Session:

When a user interacts with your Foster Framework application, a session is automatically started when the session helper object `FastVolt\Helper\Session` is imported.

```php
use FastVolt\Helper\Session;
```

After importing the Session object, declare and make use of its methods.

## Storing Data in a Session:

You can store data in a session using the `store` method

```php
// store single data
Session::store('key', 'value'); // return bool

// store multiple datas
Session::store('key', [
    'key1' => 'value',
    'key2' => 'value2'
]); // return bool
```

**A real implementation example**:

```php
$all_data = [
    'username' => 'vincent',
    'role' => 'developer'
];

Session::store('user.data', $all_data);

// get user details
$details = Session::get('user.data');

// get username data
$username = $details['username']; // return 'vincent'

// get user role
$role = $details['role']; // return 'developer'
```

## Retrieving Data from a Session:

To retrieve data from a session, you need to use the `get` session helper method.

```php
Session::get('key'); // return 'value'
```

**A real implementation example**:

```php
Session::store('username', 'oladoyinbov');

// retrieve username data
$username = Session::get('username'); // return 'oladoyinbov'
```

```php
// modify session data
Session::store('username', 'foster'); // return true
```

## Removing Data from a Session:

You can remove data from a session using the `unset` method.

```php
Session::unset('username'); // return true
```

**A real implementation example**:

```php
// store username data
Session::store('username', 'foster'); // return true

// retrieve session data
Session::get('username'); // return 'foster'

// delete session data
Session::unset('username'); // return true
```
