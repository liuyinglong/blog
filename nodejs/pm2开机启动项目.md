# pm2 开机启动项目

使用pm2添加node程序到开机启动

```shell
	#step1 启动项目
	pm2 start service.js --name service
	#step2
	pm2 save
	#step3
	pm2 startup
```