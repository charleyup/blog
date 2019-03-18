安装
```
brew install tree
```

使用
```
# 二级树，忽略node_modules目录，文件夹优先
tree -L 2 -I node_modules --dirsfirst
```
示例
```
$ brew install tree
$ tree -L 2 -I node_modules --dirsfirst

├── app
│   ├── controller
│   ├── model
│   ├── service
│   ├── views
│   ├── app.js
│   ├── config.js
│   ├── index.js
│   └── router.js
├── build
│   ├── dev.js
│   └── webpack.config.js
├── database
│   ├── migrations
│   └── config.json
├── dist
│   └── app.js
├── static
│   ├── images
│   ├── js
│   ├── lib
│   ├── style
│   └── favicon.ico
├── test
│   └── app.test.js
├── README.md
├── id_rsa_travis
├── package.json
└── yarn.lock
```
