# microservicecloud-config
microservicecloud-config demo


# application.yml #


    spring:
      profiles:
        active:
        - dev
    ---
    spring:
      profiles: dev     #开发环境
      application: 
        name: microservicecloud-config-atguigu-dev
    ---
    spring:
      profiles: test     #测试环境
      application: 
        name: microservicecloud-config-atguigu-test
    #  请保存为UTF-8格式
     
    #测试失败

# microservicecloud-config-client.yml #

	spring:
	  profiles:
	    active:
	    - dev
	---
	server: 
	  port: 8201 
	spring:
	  profiles: dev
	  application: 
	    name: microservicecloud-config-client
	eureka: 
	  client: 
	    service-url: 
	      defaultZone: http://eureka-dev.com:7001/eureka/   
	---
	server: 
	  port: 8202 
	spring:
	  profiles: test
	  application: 
	    name: microservicecloud-config-client
	eureka: 
	  client: 
	    service-url: 
	      defaultZone: http://eureka-test.com:7001/eureka/
 

# microservicecloud-config-eureka-client #

	spring: 
	profiles: 
		active: 
		- dev
	---
	server: 
	port: 7001 #注册中心占用7001端口,冒号后面必须要有空格
	
	spring: 
	profiles: dev
	application:
		name: microservicecloud-config-eureka-client
		
	eureka: 
	instance: 
		hostname: eureka7001.com #冒号后面必须要有空格
	client: 
		register-with-eureka: false #当前的eureka-server自己不注册进服务列表中
		fetch-registry: false #不通过eureka获取注册信息
		service-url: 
		defaultZone: http://eureka7001.com:7001/eureka/
	---
	server: 
	port: 7001 #注册中心占用7001端口,冒号后面必须要有空格
	
	spring: 
	profiles: test
	application:
		name: microservicecloud-config-eureka-client
		
	eureka: 
	instance: 
		hostname: eureka7001.com #冒号后面必须要有空格
	client: 
		register-with-eureka: false #当前的eureka-server自己不注册进服务列表中
		fetch-registry: false #不通过eureka获取注册信息
		service-url: 
		defaultZone: http://eureka7001.com:7001/eureka/
	
	





# microservicecloud-config-dept-client #

	spring: 
	profiles:
		active:
		- dev
	--- 
	server:
	port: 8001
	spring: 
	profiles: dev
	application: 
		name: microservicecloud-config-dept-client
	datasource:
		type: com.alibaba.druid.pool.DruidDataSource
		driver-class-name: org.gjt.mm.mysql.Driver
		url: jdbc:mysql://localhost:3306/cloudDB01
		username: root
		password: 123456
		dbcp2:
		min-idle: 5
		initial-size: 5
		max-total: 5
		max-wait-millis: 200 
	mybatis:
	config-location: classpath:mybatis/mybatis.cfg.xml
	type-aliases-package: com.wave.top.springcloud.entities
	mapper-locations:
	- classpath:mybatis/mapper/**/*.xml
	
	eureka: 
	client: #客户端注册进eureka服务列表内
		service-url: 
		defaultZone: http://eureka7001.com:7001/eureka
	instance:
		instance-id: dept-8001.com
		prefer-ip-address: true
	
	info:
	app.name: atguigu-microservicecloud-springcloudconfig01
	company.name: www.atguigu.com
	build.artifactId: $project.artifactId$
	build.version: $project.version$
	---
	server:
	port: 8001
	spring: 
	profiles: test
	application: 
		name: microservicecloud-config-dept-client
	datasource:
		type: com.alibaba.druid.pool.DruidDataSource
		driver-class-name: org.gjt.mm.mysql.Driver
		url: jdbc:mysql://localhost:3306/cloudDB02
		username: root
		password: 123456
		dbcp2:
		min-idle: 5
		initial-size: 5
		max-total: 5
		max-wait-millis: 200  
	
	
	mybatis:
	config-location: classpath:mybatis/mybatis.cfg.xml
	type-aliases-package: com.wave.top.springcloud.entities
	mapper-locations:
	- classpath:mybatis/mapper/**/*.xml
	
	eureka: 
	client: #客户端注册进eureka服务列表内
		service-url: 
		defaultZone: http://eureka7001.com:7001/eureka
	instance:
		instance-id: dept-8001.com
		prefer-ip-address: true
	
	info:
	app.name: atguigu-microservicecloud-springcloudconfig02
	company.name: www.atguigu.com
	build.artifactId: $project.artifactId$
	build.version: $project.version$
	
	
