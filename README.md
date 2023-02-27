# ChmCMS
A lightweight PHP CMS for learning.

## Change log
In previous commits, we installed npm package "axios", for send http request of client.  
Now, we add some test code, to verify that client can access to the php.  
First, we need config Vite proxy, refer to the [offical guide](https://vitejs.dev/config/server-options.html#server-proxy).  
Configration file：`client-src/vite.config.ts`
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
Now, add test code to `App.vue`.
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
Next, run: "`npm run dev`"  
Output on terminal:
```
  VITE v4.1.4  ready in 466 ms

  ➜  Local:   http://127.0.0.1:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help
```
In your browser, access: "http://127.0.0.1:5173/", and turn on "Developer tools", "Console" will output:
```
chm cms api
```
This is the output of "`public/api/index.php`":
```php
<?php
echo 'chm cms api';
```
