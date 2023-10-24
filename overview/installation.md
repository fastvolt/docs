# 📥 Installation

FastVolt is a simple, fast and scalable MVC (Model View Controller) php web framework used for building web applications. this framework is best suited for entry-level php developers because of it simplicity. our framework is your ideal companion for creating powerful, modern, and scalable web applications.

✨ **Requirements**:

* [ ] PHP 8.1 or newer
* [ ] Mysql (only if needed).
* [ ] Composer (For Package Installation).

### :robot: Installation With Composer

{% hint style="info" %}
Make sure to install [Composer](https://getcomposer.org/download/) before starting the installation process.
{% endhint %}

Run the below terminal commands to create a new project directory:

```sh
>> mkdir my-project
>> cd my-project
>> composer init
```

Use `composer` to install `FastVolt` framework to the `my-project` folder directory:

```shell
composer require fastvolt/framework
```

And for how your application will look like after installation, check:

{% content-ref url="directory-structure.md" %}
[directory-structure.md](directory-structure.md)
{% endcontent-ref %}

### 🖥️ Starting a server

Run the below command on terminal to start a server on port `8000`:

```bash
>> php -S localhost:8000 -t my-project/
```

> **NOTE**: `my-project` is the directory name or folder name where the framework was installed into.
