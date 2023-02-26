# ChmCMS
A lightweight PHP CMS for learning.

## Change log
Create project directory structure, the site will keep PHP and HTML separated,
html and php can deploy independently. Client request server by API.

Directory description:
> * server: Server source code directory, complete server, can also deploy independently.<br>
> * client-src: The client source directory, which will use Vue and compiled to static html.<br>
> * public: Root directory of the Web server. Config root directory such as Nginx to this directory.<br>
> * public/admin: The site management path, which can be accessed as http://hostname/admin.<br>
> * public/install：The install path, which can be accessed as http://hostname/install.<br>
> * public/api: API request path, accessed as http://hostname/api/~action~, or forwarded by the Nginx proxy.

Directory structure:
```
.
├─ server            // Server source directory
│  └─ index.php      // Default file for git to add directory
├─ client-src        // Client source directory
│  └─ index.html     // Default file for git
└─ public            // Web server root directory
   ├─ index.html     // The home page file
   ├─ admin          // Site management path
   │  └─ index.html  // Management entry file
   ├─ install        // The install path
   │  └─ index.html  // Install entry file
   └─ api            // API request path
      └─ index.php   // API entry file
```

Nginx config ex.：
```
server {
    listen       80;
    server_name  chmcms.local;

    root   ~~/ChmCMS/public; # Config yourself directory

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
