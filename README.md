# ChmCMS

A lightweight PHP CMS for learning.

## Change log

Now initialize the server project. Use Composer to manage PHP dependencies,
[Reference docs](https://getcomposer.org/doc/)  
Run in terminal:

```shell
cd server
composer init
```

`Composer` show config option interactively:

```
Welcome to the Composer config generator

This command will guide you through creating your composer.json config.

Package name (<vendor>/<name>) [default]: chmbird/chm-cms
Description []: A lightweight PHP CMS for learning.
Author [default <email>, n to skip]:
Minimum Stability []:
Package Type (e.g. library, project, ) []: project
License []: Apache-2.0
```

These are part of the options, that can be skipped by pressing enter and changed later.  
`Do you confirm generation [yes]?` press enter, display:

```
PSR-4 autoloading configured. Use "namespace Chmbird\ChmCms;" in src/
Include the Composer autoloader with: require 'vendor/autoload.php';
```

Finish, generate the configuration file `server/composer.json`, adjust it manually:

```
...

  "autoload": {
    "psr-4": {
      "chmbird\\chmcms\\": "src/"    // Use lower case
    }
  },
...
```

Finish, install PHP dependencies:

```shell
cd server
composer install
```

New PHP Class，`server/src/App.php`

```php
namespace chmbird\chmcms;

class App {
    ...
    public function run() {
        echo 'chm cms server app is running...';
    }
    ...
}
```

Use in `server/index.php`

```php
namespace chmbird\chmcms;

require 'vendor/autoload.php';

(new App())->run();
```

Use in `public/api/index.php`

```php
namespace chmbird\chmcms;

require '../../server/index.php';
```

Access by browser, "Console" print:

```
chm cms server app is running...
```
