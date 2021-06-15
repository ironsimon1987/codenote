

- 使用nssm替代微软的srvany

nssm安装完服务后，打开`services.msc`可以查看到自定义的服务


## 基本命令


列出已经安装配置的服务
	
	nssm list

编辑服务

	nssm edit <service-name>

安装服务
	
	nssm install <service-name>


服务管理

	nsmm start <service-name>
	nssm stop <service-name>
	nssm restart <service-name>
	nssm status <service-name>