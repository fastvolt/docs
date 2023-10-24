---
coverY: 0
---

# ☮ Password Hashing

## Initialization

```php
use FastVolt\Helper\Hash;
```

### Quick Usage

```php
$password = "mypassword";

Hash::password( $password ); // ...

Hash::verify( $password, $other_password );
```
