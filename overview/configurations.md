# 🛠 Configurations

Fastvolt configuration page is pretty straight forward, the `.env` file in your project main directory allows you to customize various settings and parameters to tailor your web application according to your project's requirements. Proper configuration ensures that your application runs smoothly and securely.

Here is how the `.env` file looks like:

{% tabs %}
{% tab title=".env" %}
```systemd
APP_NAME=FastVolt
APP_URL=http://127.0.0.1/
APP_DEBUG=true
APP_KEY=
APP_CHARSET=UTF8
APP_ENVIRONMENT=development


DB_CONNECTION=mysql
DB_HOST=localhost
DB_NAME=
DB_USERNAME=root
DB_PASSWORD=
DB_CHARSET=UTF8


MAILER=smtp
MAIL_USERNAME=
MAIL_PASSWORD=
MAIL_PORT=3306
MAIL_AUTH=true
```
{% endtab %}
{% endtabs %}

### App Essentials

#### App Name
In order to config the app name that will be used throughout your applicatiion, kindly change the `FastVolt` value to your preferred project name in `.env` file:

```systemd
APP_NAME=FastVolt
```

#### App Debug
If you are in development environment, and you want all errors you encounter to display, you can do this by enabling debug mode, this provides detailed error messages and stack traces, aiding in efficient debugging during development.

```systemd
APP_DEBUG=true
APP_ENVIRONMENT=development
```

{% hint style="warning" %}
Don't enable `debug mode` in production for security reasons.
{% endhint %}

### Retrieve Environment Variables

All environment variables in the `.env` file is all loaded into the `$_ENV` PHP super-global variable.

This environment variables can be accessed using the below format:

```php
env('app_name');
```

Or you can set a default value to ensure the env() function doesn't return `null`.

let's review the below code snippet, `Vincent Blog` will be returned as default value if the environment variable `APP_NAME` doesn't have a value or doesn't exist:

```php
env('app_name', 'Vincent Blog');
```

{% hint style="info" %}
the env() function is case-insensitive in getting environment variables.
{% endhint %}



### Getting Application Into Production

Every single time `Fastvolt` framework is installed, the `APP_ENVIRONMENT` is set to `development`, in this case, errors are displayed and dev-tools section is enabled, the development environment can be very dangerous to be enabled in production, so whenever you are moving your application to production, `APP_ENVIRONMENT` must be set to `production` and `APP_DEBUG` must be set to `false`.
