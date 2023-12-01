---
cover: >-
  https://images.unsplash.com/photo-1526374965328-7f61d4dc18c5?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw5fHxwYXNzd29yZHxlbnwwfHx8fDE3MDEzOTIyMDh8MA&ixlib=rb-4.0.3&q=85
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

$hashed_password = Hash::password($password); // ...

Hash::verify($password, $hashed_password); // true
```

