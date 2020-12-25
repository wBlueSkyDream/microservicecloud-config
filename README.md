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
 
