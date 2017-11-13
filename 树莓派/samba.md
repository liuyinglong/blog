## 安装samba
	apt-get install samba samba-common-bin 
## 制作您的samba配置文件的副本，以防以后的说明出现问题。
	cp /etc/samba/smb.conf /etc/samba/smb.conf.old
## 在RPi上的Samba服务器上启用安全性

### 注意：此部分是可选的，但强烈推荐。它强制samba服务器要求一个用户名和密码，然后允许另一台计算机连接。

编辑samba配置文件  
	nano /etc/samba/smb.conf
	
搜索标有##### Authentication #####的部分    
更改文本
  
	security = user  
	
至  

	security =用户

重新启动samba以使用新的配置文件。  

	/etc/init.d/samba restart