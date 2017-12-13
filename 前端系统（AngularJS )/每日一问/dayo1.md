springmvc简介

表现层的mvc框架,基于mvc  原理是什么样子呢?

dispatcherServlet -->根据url找handler(handlerMapping)-->因为可以是实现各种各样的接口,-->

springmvc原理

springmvc入门原理 
	


ssm整合 

spring管理pppppppppppppppppppppoooooookkkkkkkkkkkklllllll

商品信息的回显

如何接收参数?
默认支持的参数类型   key_value串  经过类型转换 赋值给controller()方法的形参

如何转发?

springmvc如何绑定包装类型?
	

springmvc如何堆集合类型参数绑定?

默认参数绑定:* servletAPI
			*model


INDEX 0  COUNT 1


聊聊requestMapping  有哪些特性?

1.url映射

	requestMapping:注解的作用就是 堆controller方法进行映射

	我们需要在 requestMapping()中指定url   对url进行路径分类


2.窄化请求映射
	为了避免url在某些情况会冲突  就可以使用 requestMapping 来指定 根url



controller方法返回值

	1.modelandview
	2.string
	3.void
	4.也可以返回  forward:"url"  地址不变  但和转发的  公用request  可以是一个action 也可以是一个jsp物理地址 相当于 struts  forward  chain
				redirect:""	'   相当于  redirect redirectAction
	5.如果都不是  就是逻辑视图的名


WEB-INF 里面的东西 是不能通过 浏览器直接访问的  因为这是项目的源目录

所有的资源  页面 字节码 都在这里面   所以只能通过controller区访问


为什么springmvc可以使用单利模式来  因为springmvc中进行参数接收

是通过形参来进行的   而形参是在方法中   没进行一次数据接收 都需要
线程在自己的私有栈中调用方法    这样的化 数据就是安全  因为每一个
线程都有自己的栈空间 

而struts2  是使用成员变量 接收数据 这样其实是有很大的缺点的

1.会造成数据拥堵  混乱   因为可能在一个类中  定义了很多成员变量 

2. 因为成员变量是共享的数据  所以每一个线程过来都会获得数据
3. 虽然struts2通过多列的这种模式  来解决多线程下 共享成员变量数据的问题
但这明显不符合 service开发的规则 


为什么有了前台校验还要有后台校验?

	因为前台校验的不安全 :  
但为什么又需要前台校验:  一个友好性 从用户的体验性出发  不用用户等到后端的响应

在前端就得到提示


后台校验:但处于对系统安全性考虑的考虑,必须对一些垃圾数据进行清除


springmvc校验方法(validate)

jsr-303 接口 

hiberanate实现了这个接口


需求:商品信息在修改时   你修改的长度不能超过30个字符长度



	5.7.3加入validator的 jar包  


如果不同的方法  想要对同一个pojo 检验不同的检验规则 怎么办?

就需要分组校验


1.批量增加
实现难点  需要将接收的数据封装到集合里面  但是handler怎么知道如何区封装这个数据呢

一般都是通过name  来  对应属性 进行封装的  所以你想封装到一个list<items> 

我的pojo的属性中  就必须有一个对应的 list<items> 来接收



2.hibernate Validate 校验

1.导包
2.配置





	