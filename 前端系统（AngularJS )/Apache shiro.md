权限控制:


	*Shiro框架学习:

	* 权限数据管理:



	*基本思想:

		*做什么?
		可以让不同的用户 访问不同的资源


每一个用户有不同的权限  每一种权限页对于多个用户


多对多               多对多         
用户-->   Role角色-->     permission

		role角色-->   菜单 menu  (可选权限  对于不同的角色可以显示不同的菜单)



登陆--> id-->角色-->menu -->



1.权限控制两种主要方式

	粗粒度URL级别的权限控制

url ---> filter(判断当前用户是否具有权限对于url)--> y/就允许访问
											--> n/权限不足

去数据库查询  用户对应的权限对应url的表  然后查询用户所有的url  遍历每一个url  看是否与当前的url匹配


request.getrequesturi;

  
缺点:


	细粒度的方法级别的控制

  @permisson("courier_add)  访问方法所需要权限信息

	通过动态代理的对象 以及 自定义的注解来实现

	访问真实对象时  会先去访问代理对象    然后查询数据库

	判断是否角有注解上 描述的权限  具有 才可以访问


url级别控制:只控制一次

方法级别:可以控制多次




自己想写权限框架 


spring security 依赖spring 使用复杂

apache shiro 

1.Authentication 认证  who are you ?

2.Authorization  授权  what can you do ?

3.Cryphtography     安全数据加密 

4.sessionManagement  会话的管理功能

5.Web  integration web 系统集成

6. interations 


ApplicationCode 用户编写代码
Subject 就是 shiro 管理的用户
SecurityManager 安全管理器，是 shiro 权限控制核心对象， 在编程时，只需要操作
Subject 方法， 底层调用 SecurityManager 方法，无需直接编程操作 SecurityManager
Realm 应用程序和安全数据之间连接器 ，应用程序 进行权限控制读取安全数据（数据
表、文件、网路 … ），通过 Realm 对象完成


pom 引入 shiro all  也可以分开引入




shiro 运行  主要流程

Application code -->subject(管理中的user)
-->SecurityManager(在编程只需要调用subject 底层自动调用)
-->Realm 应用程序  和 安全数据之间连接器, 获取案件数据来判断subject是否能够登陆

数据可以存在任何地方  对于不同的数据容器  有不痛的 


applicationContext-elasticsearch.xml


将之间解耦合?

	这个还是保存在数据库  创建一个生产者   作为参数发送数据


定时框架 多少秒 同步一次

activeMq  :针对的是一些不紧急的业务 因为它其实内部 是慢慢的一条一条去处理

只是加快了响应速度  提升了用户的体验速度   


定时quartz

多多时间 同步一次?

shiro框架配置流程; 导包-->web.xml 过滤器 --> application 管理过滤器的配置

-->

用户点击登陆-->过滤器根据用户名 密码认证:subject.login(token)-->会自动的调用

securityManagment 
securityManagment 如何去调用realm?

在application去注入bosrealm

realm: 获取用户的认证token 信息  去数据库查询 -->然后对返回来的user进行判断


如果没有此用户 就返回null

如果有  就将认证信息返回 securityManager安全管理器，自动比较返回密码和用户输入密码是否一致



自定义bosrealm 继续  AuthorizingRealm 

isNoneBlank  可变数组


subject.getprincipal();  保存用户信息


消除

1.写父类

2.写工具类  superclass   测试类 继续

对于一些重复的东西 应该有去抽取的冲动
@runwith()


@param object 
@throws:

定义一个工具类  判断指定对象所有的属性值 是否都为空;

异常处理原子:  能抛就抛 如果再抛 上边的代码是框架顶层 就处理
私有构造器

  private Objectutils(){}


	public boolean  isBlank(Object obj){
		//1.获取属性值
		Class clas = obj.getClass();
		//获取beaninfo对象
		introspectory .getBeanFo();

		beaninfo

		readmethod 
		
		
		writemethod
			
		
		return false;
				
	}

elasticSearch

new 一个 junit test case

获取了getClass   需要将class排除

continue;

erro打出来是红的

其实还有更简单的方案

BeanUtil.describe(); 

获取一个对象所有的 key value ;

然后判断键是否优质

map.getValues();


@Target(ElementType:)
源注解
@Target:作用目标


@Retention:生效时机  eg:override 编译时生效   检查语法


@Documented

cmd  javadoc hehe.java


@inherited  :定义了之后  父类的注解可以被子类继承









 







