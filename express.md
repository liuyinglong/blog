# express 判断不同的设备访问，并根据不同的设备使用不同的静态页面

## 判断不同的设备

需求：公司官网有pc和移动端两个不同的设备，访问首页时，根据不同的设备类型来返回不同的静态文件资源。

实现：

使用express作为静态资源服务器,express-static处理静态文件,根据不同的文件类型来设置不同的缓存策略。

```javascript
//判断当前环境类型，根据不同的环境使用不同文件目录
const isDev = process.env.NODE_ENV === "development";
let pcStaticPath = isDev ? "/your/pc/dev/path" : "/your/pc/production/path";
let mobileStaticPath = isDev ? "/your/mobile/dev/path" : "/your/mobile/production/path";

let staticOptions = {
    //设置缓存策略
    setHeaders: function (res, path, stat) {
        if (/\.(js|css|jpg|gif|png|svg|ico|eot|ttf|woff|woff2|otf)$/.test(path)) {
            res.set("cache-control","public,max-age=2592000")
        }
        if (/\.(html)$/.test(path)) {
            res.set("cache-control","no-cache,no-store")
        }

    }
}
app.use(function (req, res, next) {
    let deviceAgent = req.headers["user-agent"].toLowerCase();
    let agentID = deviceAgent.match(/(iphone|ipod|ipad|android)/)//获取设备类型
    if (agentID) {
        express.static(mobileStaticPath, staticOptions)(req, res, next);    //手机网站
    } else {
        express.static(pcStaticPath, staticOptions)(req, res, next);     //PC网站
    }
});
```



