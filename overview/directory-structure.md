# 📂 Directory Structure

Here is how FastVolt directory structure looks like after installation:

```iecst
├── config                  # Configuration files (routes.php, site.php)
├── public                  # Web server files (index.php)
├── resources               # server resources (css, js, images, ...)
├── routes                  # request routing files
    ├── api.route.php       # Api routes
│   ├── main.route.php      # Main application routes
│   ├── dev.route.php       # Devtools routes
├── src                     # Application core source code
├── storage                 # Server storage
│   ├── cache               # Cache files
│   ├── error_log           # Default error logs
│   ├── recovery            # Application Recovery files storage
│   ├── smarty              # Default smarty template cache storage
├── views                   # Application templates are stored here
│   ├── index.php           # Default Index Page
│   ├── 404.php             # 404 Page
```

