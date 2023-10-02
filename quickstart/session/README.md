# ⭐ Session

## Initialization

```php
use FastVolt\Helper\Session;
```

### Quick Usage

```php
# store new session
Session::store('user', 'vincent'); // true

# retrieve stored session
Session::get('user'); // vincent

# unset stored session
Session::unset('user'); // true

# delete all session
Session::destroy(); // void
```


In FastVolt Framework, the PHP session handling mechanism allows you to store and manage user-specific data across multiple requests and sessions. 

Sessions are a way to maintain stateful information about a user's interactions with a web application. 



## Storing Data in a Session:

You can store data in a session using the `store` method

```php
// store single data
Session::store('key', 'value'); // return bool

// store multiple value datas
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
echo $details['username']; // return 'vincent'

// get user role
echo $details['role']; // return 'developer'
```
The `store` session method accept only two parameters:
- `key`: *string*
- `value`: *mixed*.

<br>

## Retrieving Data from a Session:

To retrieve data from a session, you need to use the `get` session helper method.

```php
Session::get('key'); // return 'value'
```
The `get` session method only accept two parameters:

- `session_key`: *string*.

  

**A real implementation example**:

```php
Route::post('/auth', function () {

   # check if required header method is POST request
  if(request()->is_post()) {

     # get form datas
     $form = request()->input();

     # validate form post request datas
     request()->validate(
      'username' => 'required|min:2'
     );

       # return error message if validation process encountered any errors
      if( request()->validate_errors() ){
          return request ()->validate_errors();
       }

      # check if username is stored in session successfully
      if( Session::store('user.name', $form->username) ){
         # redirect to dashboard
         request()->redirect('/dashboard', 301);
      } 
   }
}
```

// dashboard
```php
Route::get('/dashboard', function () {

   # request session data
   $username = Session::get('username');

   # display retrieved session data
   if( $username ) {
      echo $username; 
    }
   
}
```

<br>


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
The `unset` session request method only accept one parameter:
- `session_key`: *string*.

<br>


## Destroying All Session
In order to destroy all session in an application, here is how to do it using the `destroy' session method:

```php
Session::destroy(): void;
```
> `destroy` method accepts no parameter but returns *null* | *void*.
