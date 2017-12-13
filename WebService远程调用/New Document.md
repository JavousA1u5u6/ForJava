webService

主要是用来解决 分布式系统之间的数据通信问题


webService在我看来就是一个服务的中间商  
很多个系统，进行分布的部署，分布的系统数据通信 解决技术就是 WebService
想要实现 webService 就可以采用 codeFirst 和 wsdl first 来轻松实现web Service 的发布 和使用
CXF:是目前主流的框架 apache提供 

我们需要某种服务 就可以调用 webservice 来提供 比如:天气的服务接口

服务器如何发布服务?
1.服务实现对象
2.发布服务地址
3.发布服务


客户端要调用接口??



服务端响应数据?


wsdsl展示有什么服务



而 cxf  webserVice开发 主要分为两种方式 WS .RS

jax-ws  和 jax -rs
java api forXML 
java api forRESTful

底层的通信协议不一样  传的其实就是XML格式 基于soap协议 ( 一种简单的数据格式)

jax-rs 传输数据  传输xml和json  基于 http协议


jax-ws


md5加密

1.见一个独立的项目  maven-jar

http://localhost:9999/userService?wsdl

C:\Users\JavousAiMe\Desktop\新建文件夹

ws -d xxxxx    -client xxxx  生成一个java代码放在这个目录中


software过期后 如何删除注册表 来继续使用软件?

  regedit -->HKEY_CURRENT_USER\Software\Allround Automations -->

用jaxws 的原因是底层帮助创建了 prxy对象

CXf-ws-spring 整合

服务端 spring都做了哪些事

ioc:将 IUservice接口  以及adress 配置实现类


常用 WebService Hessian  dubbo ;


JAX-RS

什么是restful风格
		

为什么学习这种风格,有什么好处?
	软件的编写更加简洁  只需要一个路径完成CRUD 支持多种消息格式 基于HTTP
	更易于实现缓冲机制

tomcat 

第一次就会把数据缓冲到客户端

第二次服务器发现还是没有修改过的资源 就会从客户端的缓冲中获取 




什么效果?

	根据不同的请求方式 	服务器可得知进行CRUD哪种操作

http://+user  查询所有


http://+user+1 查询1客户的信息

怎么发送 post /delete/put

隐藏了

xml根元素

@XMLRootElement(name="Car");

指定序列化 对象名字
	能够生成哪种格式的格式数据传递过来数据数据格式
@Produces(return)

	能够处理客户端传递过来的数据格式
 @Consumes(parameter)


如果项实现某一条数据单独查询

	需要使用 url

1.明确一件事  使用webService 就是为了用多系统之间进行数据通信
比如: 一个系统获取另一个系统的数据 
2.比如?  如何通信呢  这里使用了动态代理创建代理对象 来进行增强
使用代理对象 来调用 实际上调取的还是服务端的服务对象
	
所以在服务端需要提供一系列增删改查的方法
get()获取数据
post()添加
put()修改
delete()删除 



在服务端 只需要创建一个代理对象 来调用方法获取
cxf_rs_spring  基于xml/json进行数据通信 最后实际就是拼接处一个xml文件
1.配置webxml  基于web访问
2.到包 ws核心包   
3.导入实体类  配置注解xmlRootelement(name="Car") 表明xml的根元素
4.配置service  接口   
@Produces("*/*") 能够生成哪种格式的格式数据传递过来数据数据格式
@POST
	@Path("/user")
	@Consumes({ "application/xml", "application/json" })
5配置实现类 




使用spring官邸对象 并且可以自动创建代理对象





