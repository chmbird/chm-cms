# ChmCMS

一个用于学习的轻量级 PHP-CMS。

## 变更日志

现在，初始化服务端项目。使用`Composer`来管理PHP依赖，[参考文档](https://docs.phpcomposer.com/)  
命令行运行：

```shell
cd server
composer init
```

`Composer`提供一个交互式配置选项：

```
Welcome to the Composer config generator

This command will guide you through creating your composer.json config.

Package name (<vendor>/<name>) [default]: chmbird/chm-cms  // 项目命名
Description []: A lightweight PHP CMS for learning.        // 项目描述
Author [default <email>, n to skip]:                       // 输入作者名字和Email
Minimum Stability []:                                      // 最低稳定性
Package Type (e.g. library, project, ) []: project         // 项目类型
License []: Apache-2.0                                     // 许可
```

以上是部分选项，可以一路回车跳过，稍后再改。  
`Do you confirm generation [yes]?`，确认后，显示：

```
PSR-4 autoloading configured. Use "namespace Chmbird\ChmCms;" in src/
Include the Composer autoloader with: require 'vendor/autoload.php';
```

完成，生成`server/composer.json`配置文件，手动调整一下：

```
...

  "autoload": {
    "psr-4": {
      "chmbird\\chmcms\\": "src/"    // 改为小写
    }
  },
...
```

配置完成，安装PHP依赖：

```shell
cd server
composer install
```

新建PHP Class，`server/src/App.php`

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

引用，`server/index.php`：

```php
namespace chmbird\chmcms;

require 'vendor/autoload.php';

(new App())->run();
```

API引用，`public/api/index.php`：

```php
namespace chmbird\chmcms;

require '../../server/index.php';
```

前端访问，“Console”显示：

```
chm cms server app is running...
```
