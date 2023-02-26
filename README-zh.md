# ChmCMS
一个用于学习的轻量级 PHP-CMS。

## 变更日志
创建项目目录结构，网站将采用前后端分离架构，Html静态部署。

目录说明：
> * server：服务端源码目录，完整服务端，未来也可独立部署<br>
> * client-src：客户端源码目录，将使用Vue构建，编译静态html<br>
> * public：Web server根目录，配置Nginx等根目录到此<br>
> * public/admin：后台管理路径，以http://hostname/admin访问<br>
> * public/install：安装路径，以http://hostname/install访问<br>
> * public/api：API请求路径，以http://hostname/api/~action~访问，也可配置Nginx代理转发<br>

目录结构：
```
.
├─ server            // 服务端源码目录
│  └─ index.php      // 默认文件，方便git添加目录
├─ client-src        // 客户端源码目录
│  └─ index.html     // 默认文件，for git
└─ public            // Web server根目录
   ├─ index.html     // 主页文件
   ├─ admin          // 后台管理路径
   │  └─ index.html  // 后台管理入口
   ├─ install        // 安装路径
   │  └─ index.html  // 安装入口
   └─ api            // API请求路径
      └─ index.php   // API入口
```

Nginx配置示例：
```
server {
    listen       80;
    server_name  chmcms.local;

    root   ~~/ChmCMS/public; # 设置自己的目录

    location / {
        # root   ~~/ChmCMS/public;
        index  index.php index.html;
    }

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    location ~ \.php$ {
        # root           ~~/ChmCMS/public;
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
    }
}
```
