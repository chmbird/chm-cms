# ChmCMS
一个用于学习的轻量级 PHP-CMS。

## 变更日志
在前面的提交中，我们安装了npm包“axios”，用于前端发送http请求。  
现在，我们添加测试代码，验证一下，前端可以访问到php。  
首先，我们需要配置一下Vite的代理，参考[官方文档](https://cn.vitejs.dev/config/server-options.html#server-proxy)  
配置文件：`client-src/vite.config.ts`
```
const targetHost = 'http://chmcms.local'

server: {
  proxy: {
    '/api/': {
      target: targetHost,
      changeOrigin: true
    }
  }
}
```
现在，在`App.vue`中添加测试代码
```
import axios from 'axios'
import { onMounted } from "vue"

function request() {
  axios.get('/api/').then(res => {
    console.log(res.data)
  }).catch(err => {
    console.log(err)
  })
}

onMounted(() => {
  request()
})
```
接下来，运行：“`npm run dev`”  
终端输出：
```
  VITE v4.1.4  ready in 466 ms

  ➜  Local:   http://127.0.0.1:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help
```
在浏览器里访问：“http://127.0.0.1:5173/”，并打开“开发者工具”，“Console”将会显示：
```
chm cms api
```
这正是`public/api/index.php`的输出：
```php
<?php
echo 'chm cms api';
```
