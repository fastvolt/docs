# 🕹 Validation

Request form validation is the process in which data sent by end-users to the application are been properly verified. This process ensures that users submit accurate data in the required format, safeguarding the application from potentially harmful form input.

Validation is done by passing different rules into the request `validate()` method.:

{% tabs %}
{% tab title="Fastvolt" %}
```php
$validate = request()->validate([
    'username' => 'required|max:20', // form_field_name => 'rules'
    'password' => 'required'
]);
```
{% endtab %}

{% tab title="Core PHP" %}
<pre class="language-php"><code class="lang-php">if (! isset($_POST['username']) || strlen($_POST['username']) > 20 ) {
   return 'invalid username';
}

<strong>if (! isset($_POST['password']) ) {
</strong>   return 'invalid password';
}

//...
</code></pre>
{% endtab %}
{% endtabs %}



### Usage Sample

Request validation works hand-in-hand with application controller, here is a usage example of this wonderful feature:

{% tabs %}
{% tab title="LoginController.php" %}
```php
<?php

declare(strict_types=1);

namespace App\Http\Controller;

use FastVolt\Core\Controller;

use App\Model\User;

class CompanyController extends Controller
{
   # check if required header method is POST request
  if(request()->is_post()) {

     # get form datas
     $form = request()->input();

     # validate form post request datas
     $validate = request()->validate(
        'username' => 'required|min:2'
     );

       # return error message if validation process encountered any errors
     if( $validate->has_errors() ){
          return $validate->errors();
       }
       
       // ....
   }
}
```
{% endtab %}
{% endtabs %}



### Available Validation Filters

* `required` - this filter makes sure the submitted form value isn't empty.
* `min:{value}` - this filter makes sure the submitted form value has the specified minimum value length.
* `max:{value}` - this filter makes sure the submitted form value has the specified maximum value length.
* `is_email` - this filter makes sure the submitted form value is a valid email address.
* `is_string` - this filter makes sure the submitted form value is a valid string.
* `match:{value}` - this filter checks the submitted form value if it matches another form value.
* `unique:{ModelName}` - this filter check the model database row and see if form value is a unique value (useful for checking if form value already exist in db row).



### Custom Error Messages

If you already notice fastvolt auto-generate error messages for each validations, which may not be very pleasant for many developers, so there is a method to add custom error messages for request validation.

Here is an example to add basic custom error message to request `validate` method:

```php
$validate = request()->validate([
   'username' => 'required|max:20'
],
// custom validation messages 
[
   'username' => 'Username field is invalid!'
]);

echo $validate->errors(); // Username field is invalid!
```

&#x20;

There is also another method to breakdown the error messages into segment (based on each filters):

```php
$validate = request()->validate([
   'username' => 'required|max:20'
], 
// custom validation messages
[
   'username.required' => 'Username field is invalid!',
   'username.max' => 'Username value must be lesser than 40 characters'
]);
```

