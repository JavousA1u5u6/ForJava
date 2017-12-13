1、 Authentication 认证 ---- 用户登录，身份识别 who are you?
2、 Authorization 授权 --- 用户具有哪些权限、角色 what can you do ?
3、 Cryptography 安全数据加密
4、 Session Management 会话管理
5、 Web Integration web 系统集成
6、 Interations 集成其它应用，spring、缓存框架

ApplicationCode 用户编写代码
Subject 就是 shiro 管理的用户
SecurityManager 安全管理器，是 shiro 权限控制核心对象， 在编程时，只需要操作
Subject 方法， 底层调用 SecurityManager 方法，无需直接编程操作 SecurityManager
Realm 应用程序和安全数据之间连接器 ，应用程序 进行权限控制读取安全数据（数据
表、文件、网路 … ），通过 Realm 对象完成


anon 未认证可以访问
authc 认证后可以访问
perms 需要特定权限才能访问
roles 需要特定角色才能访问
user 需要特定用户才能访问
port 需要特定端口才能访问
reset 根据指定 HTTP 请求访问才能访问

访问 courier.html 时，因为需要特别权限 调用 自定义 Realm 的 doGetAuthorizationInfo
进行授权，如果没有权限，跳转
<property name="unauthorizedUrl" value="/unauthorized.html" />
访问courier.html  此资源被拦截 需要相应的授权 才能访问

就会告诉安全管理器 去找realm  查询此用户的相应权限   realm 可以返回一个map 

里面定义了很多信息  判断这个map中是否有 此条请求的信息  有就放行


hql :  select from role r inner join fetch  user  u where u,id = ?

hql :  from  permission p  inner join fetch  p .roles  r 

		inner join  fetch r.users u where u.id = ?

hql : from menu m inner join fetch m.users. u where u.id =?

返回一个数组  需要一个集合 

sql: select * from t_role t 

left join  t_user_role  on t1.id= t2.role_id 

left join  t user t3 on t2.cu_user_id = t3.cid

where t3.c_id = 2001;

@Querynative Query =true;

 doGetAuthorizationInfo

需要将之间学习的一些hiberate查询熟悉下


对sql 进行整理 
最快定位

对各个中间件的配置 怎么使用 进行整理  

对学习的一些小技术 小工具进行整理


注解的方式来实现方法级别细粒度


1.激活注解
	创痛spring AOP配置 


	requirePermissions

事务管理时基于代理对象来管理的

但是它会对目标对象实现的接口创建一个新的实现类

而这个新的实现类 并没有此注解 

所以会发送  注解失效的情况

注解问题: 业务层对象被事务管理   底层时基于代理完成

当目标对象有接口  代理对象就是对接口代理 

比如说你访问代理对象 来访问这个接口方法

但是实际的并没有这个权限注解

需要使用cglib  并加上一个@inherited   定义注解可继承

所以需要 首先让配置的shiro注解能够被扫描

我们的注解要想生效  就必须能够被扫描
这种扫描在底层时通过aop 

除了错可以配

(友好页面)
erro page 


exceptoiotype  需要配置全类名


location /xxxx.html 

当配置了 

@RequiresPermissions("courie_add")
	public void save(Courier courier) {
		courierRepository.save(courier);
	}

Subject does not have permission [courie_add]

用户没有这个权限

当出现此异常时  应该为用户友好的提示以下 而不是直接显示500异常


自定义 标签的显示

jsp :能够更加精细化  对页面元素的显示进行控制

area:add  :冒号代表子权限

系统里面又多少资源?

	我也没有数过  数据库中的资源数据和诺

我们这个项目大概一共有20多个 模块

我做的这个模块就有12张表 

第二个模块 有8张

你的权限表有多少个记录呢>

	500来条记录

每一个模块都有一些小功能  每一个功能 都对应一个权权限记录

有时候最多一天写 500多行的有效代码


最繁琐的地方就是在xml中 配置相关url 的 权限设置 耗费的大量的精力去针对性的去添加
 

第一种:配置web.xml 的shiroFilter拦截

	在application.xml  与filter 同名的bean ;

	里面 配置拦截的 控制规则   url粗粒度界别


 select menu0_.C_ID as C_ID1_5_0_, role2_.C_ID as C_ID1_9_1_, user4_.C_ID as C_ID1_16_2_, menu0_.C_DESCRIPTION as C_DESCRIPTION2_5_0_, menu0_.C_NAME as C_NAME3_5_0_, menu0_.C_PAGE as C_PAGE4_5_0_, menu0_.C_PID as C_PID6_5_0_, menu0_.C_PRIORITY as C_PRIORITY5_5_0_, role2_.C_DESCRIPTION as C_DESCRIPTION2_9_1_, role2_.C_KEYWORD as C_KEYWORD3_9_1_, role2_.C_NAME as C_NAME4_9_1_, roles1_.C_MENU_ID as C_MENU_ID2_10_0__, roles1_.C_ROLE_ID as C_ROLE_ID1_10_0__, user4_.C_BIRTHDAY as C_BIRTHDAY2_16_2_, user4_.C_GENDER as C_GENDER3_16_2_, user4_.C_NICKNA4_.C_REMARK as C_REMARK6_16_2_, user4_.C_STATION as C_STATION7_16_2_, user4_.C_TELEPHONE as C_TELEPHONE8_ME as C_NICKNAME4_16_2_, user4_.C_PASSWORD as C_PASSWORD5_16_2_, user16_2_, user4_.C_USERNAME as C_USERNAME9_16_2_, users3_.C_ROLE_ID as C_ROLE_ID2_17_1__, users3_.C_USER_ID as C_USER_ID1_17_1__ from T_MENU menu0_ inner join T_ROLE_MENU roles1_ on menu0_.C_ID=roles1_.C_MENU_ID inner join T_ROLE role2_ on roles1_.C_ROLE_ID=role2_.C_ID inner join T_USER_ROLE users3_ on role2_.C_ID=users3_.C_ROLE_ID inner join T_USER user4_ on users3_.C_USER_ID=user4_.C_ID where user4_.C_ID=? order by menu0_.C_PRIORITY


menu t_menu_role role t_user_role user 5张表

通过用户id 查询 菜单
select t_menu t1 
inner join t_role_menu t2 
on t1.id = t2._menu_id 
innder join t_role t3 
on t2.role_id = t3.id
innder join t_user_role t4
on t3.id = t4.role_id
inner join t_user t5
on t4.id = t5.user_id
where id =? order by t1.priority


学生 组长 组id 
		id    pid
学生1  1  
学生2  11      1
学生3	12     1		
学生4    13     1

学生受组长的管理

一个组长 对应有多个学生

一个学生 只有一个组长


老师 一个问题:

activeMq:解决高并发  

生产者有两种 topic  queue

topic 生产的消息 能被多个消费者线程进行消费
queue 生产的消息 只能被一个消费者线程进行消费

最简单的一个列子: 用户在注册页面 通过手机号 进行注册 我们需要对用户的手机号发送验证码


那么仿造一个场景:当多个用户都进行注册操作 -->后台创建生产者 往 生产者进程里 添加数据

 消费者 从消息进程中  获取消息进行消费

如果使用多个消费者去消费  会加快效率码

 









