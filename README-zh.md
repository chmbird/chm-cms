# ChmCMS
一个用于学习的轻量级 PHP-CMS。

## 变更日志
初始化前端部分项目源码，使用Vue@3，采用Vite构建。

直接使用命令：
```shell
cd client-src
npm init vue@latest .
```
Vite显示一个对话形式设置Vue配置(括号是设置的值)：
```
Vue.js - The Progressive JavaScript Framework
✔ Current directory is not empty. Remove existing files and continue? (yes)
✔ Package name: (chm-cms)
✔ Add TypeScript? (Yes)
✔ Add JSX Support? (No)
✔ Add Vue Router for Single Page Application development? (Yes)
✔ Add Pinia for state management? (Yes)
✔ Add Vitest for Unit Testing? (Yes)
✔ Add an End-to-End Testing Solution? (No)
✔ Add ESLint for code quality? (Yes)
✔ Add Prettier for code formatting? (Yes)
```
解释一下：  
项目使用TS开发前端，所以“TypeScript”选“Yes”，其它都是非必选项，可以都选No，后期再加。
