最好在黑窗口  不会照成图形化工具导入大量数据会卡死的情况


show 

create database

user database 

source 指定脚本位置 


maven 编译好了之后 都在 target    classpath就是class文件下的目录

   占位符 ?  是拿你传入的参数的整体 去数据对应的字段 去匹配 sql语句  与参数  两部分

	拼接 是事先去拼接 来组合sql语句 去数据库查询   只有一部分  肯定可以执行成功

指定的是单条的记录

 username = '' and password = '' or '1'= '1';


#{} 任意


${}  指定value  字符串   

如何输入参数是一个简单的pojo 

#{}

${},String类型别忘了拼接两个单引号
	

设置回显id参数  keycolumn  genkey   key property  


uuid至少36位  测试时需要注意字段的位数 rpa


select now();  


所有的非静态同步方法用的都是同一把锁——实例对象本身，也就是说如果一个实例对象的非静态同步方法获取锁后，该实例对象的其他非静态同步方法必须等待获取锁的方法释放锁后才能获取锁，可是别的实例对象的非静态同步方法因为跟该实例对象的非静态同步方法用的是不同的锁，所以毋须等待该实例对象已获取锁的非静态同步方法释放锁就可以获取他们自己的锁。
　　而所有的静态同步方法用的也是同一把锁——类对象本身，这两把锁是两个不同的对象，所以静态同步方法与非静态同步方法之间是不会有竞态条件的。但是一旦一个静态同步方法获取锁后，其他的静态同步方法都必须等待该方法释放锁后才能获取锁，而不管是同一个实例对象的静态同步方法之间，还是不同的实例对象的静态同步方法之间，只要它们同一个类的实例对象！

java中变量的存储位置

1.寄存器：最快的存储区, 由编译器根据需求进行分配,我们在程序中无法控制. 
2. 栈：存放基本类型的变量数据和对象的引用，但对象本身不存放在栈中，而是存放在堆（new 出来的对象）或者常量池中（字符串常量对象存放在常量池中。） 
3. 堆：存放所有new出来的对象。 
4. 静态域：存放静态成员（static定义的） 
5. 常量池：存放字符串常量和基本类型常量（public static final）。 
6. 非RAM存储：硬盘等永久存储空间 

现在每当一个线程 就会创建它私有的jvm栈 
栈里面存的是什么呢?
	这时每一个线程独享的
	当前线程中 存局部基本类型的变量(8打基本数据类型 boolean、char、byte、short、int、long、float、double)
	部分的返回记过  以及执行堆的  内存地址值    

  进来调用 delete 都会    
在delete放大里面会干这么几件事情 
去读取加载全局配置

 Opening JDBC Connection
DEBUG [Thread-1] - Opening JDBC Connection 打开连接池
DEBUG [Thread-0] - Created connection 1225868904.  创建一个连接
DEBUG [Thread-0] - Setting autocommit to false on JDBC Connection [com.mysql.jdbc.JDBC4Connection@49114668]
DEBUG [Thread-0] - ==>  Preparing: update user set username=?,birthday=?,sex=?,address=? where id=? 预编译语句
DEBUG [Thread-1] - Created connection 1337919446. 又创建了一个连接
DEBUG [Thread-1] - Setting autocommit to false on JDBC Connection [com.mysql.jdbc.JDBC4Connection@4fbf07d6]
DEBUG [Thread-1] - ==>  Preparing: update user set username=?,birthday=?,sex=?,address=? where id=? 
DEBUG [Thread-0] - ==> Parameters: 小黑黑1(String), 2017-12-06 21:08:48.595(Timestamp), 女1(String), 松花江上游1(String), 161(Integer)
DEBUG [Thread-1] - ==> Parameters: 小黑黑1(String), 2017-12-06 21:08:48.595(Timestamp), 女1(String), 松花江上游1(String), 161(Integer)
DEBUG [Thread-1] - <==    Updates: 0
DEBUG [Thread-1] - Committing JDBC Connection [com.mysql.jdbc.JDBC4Connection@4fbf07d6]
DEBUG [Thread-0] - <==    Updates: 0
DEBUG [Thread-1] - Resetting autocommit to true on JDBC Connection [com.mysql.jdbc.JDBC4Connection@4fbf07d6]
DEBUG [Thread-0] - Committing JDBC Connection [com.mysql.jdbc.JDBC4Connection@49114668]
DEBUG [Thread-1] - Closing JDBC Connection [com.mysql.jdbc.JDBC4Connection@4fbf07d6]
DEBUG [Thread-0] - Resetting autocommit to true on JDBC Connection [com.mysql.jdbc.JDBC4Connection@49114668]
DEBUG [Thread-1] - Returned connection 1337919446 to pool.
DEBUG [Thread-0] - Closing JDBC Connection [com.mysql.jdbc.JDBC4Connection@49114668]
DEBUG [Thread-0] - Returned connection 1225868904 to pool.



运行结果就是 in fun 和 in fun2 交替出现，就是没有 in fun1。 
只要运行 fun 的线程不交出锁，fun1 就无法被调用，因为他们都是共享了 Class object 的锁。



要根据ognl表达式来导航属性



练以下 如何传入一个map

动态sql if(test = "ognl导航属性")

		where :sql 中的where 可以去除and 第一个and 

sql : 可以定义sql片段  对公共抽取  include refid 引用; 一般不要套where  就在外面套

foreach: 循环


需求:根据用户名 或者 性别, 多个id查询用户列表

	 以上的条件参数 封装 到一个包装类型的pojo

联系动态slq  比如插叙 用户的id为 1 2 3 用户名是  xxx 地址 是xxx

sql 语句中的  username ,dsddsds 也可以抽



使用mybatsi进行关联查询

如何进行多表查询?
	

一对yi:

 根据订单查询用户  只查询用户地址  和 用户信息 
		一个订单只能对应一个用户
	sql语句怎么写?
		sql 92
		select orders.*,username from user u , order o where u.id = o.uid (+):mysql不适用 
	查询到的数据怎么输出映射

一对多


内链接与外链接有什么区别?

	sql99 
	select orders.*,username from user u inner join  order o where u.id on o.uid

左边的记录 必须全部出现  右边的没有关联 用null 代替  右关联多的全部出现

如何封装数据呢?12/8/2017 4:18:34 PM 

o.*查询订单表的所有字段

多表查询的数据 是两表交集的数据 没有pojo 匹配  就重写创建了一个pojo继承order


用hashmap  就不用再定义pojo    将一些信息封装到order 再将一些信息封装到关联的user

如何定义一对多的查询呢?

	通过订单 查询订单中所有的订单详情

	
查询的数据 有哪些数据呢? 

如何把这些数据分开 


  设计  订单表     订单详情表



  set()

如果不使用mybatis
	String sql = "select * from  user"
		if(user.getusername!=null){
			sql +="where";
			if(user.getusername!=null){
		sql += " username = ?"
	}else{
		sql +="where";
		
	}
			}
		}if(user.getaddress!=null){
      sql +=" address =?" 


<!-- 思考：如何拼接
				 AND (id=1 OR id=10 OR id=16)
				 -->
<foreach collection="ids" item="id" open=" AND  ( id= " close=")" separator="OR id=">
						
							#{id}
				</foreach>	

什么时候使用resulttype?
	如果查出的数据结果集的字段  与现有pojo中的属性一致  就可以使用resulttype  优点:使用比较简便


什么时候使用resultmap?
	如果查出的数据结果集的字段  与现有pojo的属性不一致  并要求 需要映射出来  就可以使用resultmap


什么时候使用paraterMap?

	当查询的参数 有多个 并且无法封装到现有pojo 的属性  可以使用 paramerMap;


什么时候使用动态sql?

	在很多时候  我们的sql 语句  需要根据 具体的需求 去动态改变时  就可以使用动态标签去凭借

	if  判断条件是否成立
	
	foreach

	where

关于多表查询查到的数据 如何根据要求封装?
	1.创建 对应结果集字段pojo类 进行封装
			
	2.使用resultmap进行映射



jdk动态代理 对当前接口 创建实现类 

代理类如何获取select 语句 去执行


多对多


connection 套connection 


assocition     javatyoe


conn    oftype

理解清除实体之间的关系  

用户里面有订单  订单里面有详情  详情里面有商品

多对多的思考?
	resultMap就是实现高级映射  如果你对结果集有高级映射的需求

将一个列表数据映射到pojo的list属性


使用resultMap还有一个很重要的特性   延时加载




1.分析多关系 

2. 在映射语句中编写sql语句

3.使用resultMAP来完成一个感激映射

什么是


@resource 先根据名称拿  然后更具类型拿  可以指定从容器

=

@Autowired  可以将@qualifier( )


基于某一个表进行增删改查  


怎么根据测试类 生成测试方法



			
