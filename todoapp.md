# Create A Simple Todo App

A simple todo app requires basic knowledge of CRUD (Create, Read, Update, Delete) in PHP, but FastVolt simplify this process by introducing some basic helpers function and objects to help you through the creation process.

## Step 1: Installation

Install FastVolt using Composer

```cmd
composer require FastVolt/core
```

## Step 2: Configuration

Fill-in the required configurations in the `.env` file.\
\
**NOTE**: this step requires the following configuration to be properly set.

* [x] APP\_URL - this environment variable value is set to localhost: `127.0.0.1:8080` by default, you can change this to your server address.
* [x] APP\_ENVIRONMENT - change this environment variable value to `development`, in order to enable the DevTool section.

## STEP 3: Access DevTools

FastVolt helps in simplifying some basic tasks like creating controllers, model and database tables. but based on this simple application, we only need the controller to complete the task. Enter your search bar and input this address: `127.0.0.1/devtool/`.

> **Note**: 127.0.0.1 should be your server address.

\
The web address should get you the devtool interface where you can access the controller section.

## Create Resources Controller

From the controller section, create resources controller (this type of controller automatically generates the CRUD functions). in our case, we will be generating a controller with the name `Todo`.

When your controller generates, you should be able to access it in this directory: `app/Http/Controller/TodoController.php`

\
in our generated Todo Controller, we have the \`index\`, \`create\`, \`update\`, \`edit\`, \`show\` and \`destroy\` methods respectively.\
The \`index\` method will handle the application front view.

So, Let's get started.

## Create `Index` Template

Create a `index.tpl` file in `views/` directory.

```tpl
<h2>ToDo List</h2>

<section>

<ul>

<li></li>

</ul>

</section>
```

> **Note**: The above code only shows how our application front-page can look like, there is no logic to it yet.

## Handle `Index` Template

So, to display our index template, we need to create a logic to handle and render the `index.tpl` template.

Navigate and Edit File: `app/Http/Controller/TodoController.php`, in **index** method.

```php
public function index(): ?Views
{
   // this will render our created index views template
   $this->render('index.tpl');
}
```
