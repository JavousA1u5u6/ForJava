后台获取到邮箱之后会进行一次判断

根据邮箱的  判断是否包含@163.com		qq.com

调用不同的邮件服务

redis nosql 数据库 not only sql 

key-value 数据库 key-value 内存

memCache


对应使用需要jedis(C语言写的) 驱动

为什么需要飞关系型数据库呢

		因为关系型数据库 对于获取数据还行  但一旦进行高并发的读写操作  就会由很大的压力 影响系统的响应能力

		
web1.0

就早期的网易新闻啊  还有一些新浪 网  只能在上面浏览 浏览信息

web2.0

像现在的微博 朋友圈  我们可以进行互动 点赞  者依靠传统的关系型数据库就不行了

非关系型数据库就此兴起   

这是一个和传统数据库完全不同的数据库，主要优势能够简单的解决关系型数据库中管理不同类型数据麻烦，以及排序整合的常见操作的性能问题等。 

  所以我们一般称呼这种也叫   高可用性的键值商店”


现在一些大型应用  像淘宝 腾讯 百度 等 google  yahoo nasa   动不动每天都可能由上亿  几十亿的数据流动  使用关系型数据库 会由很大的读写亚拉  

需要管理不同的数据类型  以及排序整合操作的性能问题

A:生产者  bos项目平台  提前约定好  

所以非关系型数据库也是web2.0必定会衍生出的产物

activeMQ 消息队列   解决 高并发访问  加快响应速度  后台不用处理接口服务    只需要将数据交给activeMQ 的生产者  再由消费者接收  带调用
服务的服务器   在这个途中  用户是可以继续操作 无需等待   中间时间不再在后台中耗费 

中转站 


发短信项目平台 B:消费者 

之前在项目中必须自己去调用服务  需要耗费一定的时间

客户接收到响应之后才能操作


现在往中转站发送了一个请求 sms  不必自己再去调用服务

客户可以接着操作  


说说你理解的集群?

	集群就是多个相互独立的计算机  通过中央系统统一的的管理  分配相同的任务    客户与计算机的交互 就是客户跟以群计算机的交互 
有很高的可用性 和 伸缩性  通过前端负载均衡

说说你理解的分布式?

	分布式就是讲一个  任务 分层多个模块 架设到多个子节点上   每个子节点计算机 有着不同的任务  各节点之间通过网络通信

区别:就好比一个餐馆  生意不行的时候  只有一个炒菜师傅     后来生意好了  又招了一个炒菜师傅  它两的关系 就好比集群
后来生意更加红火  又找了一个配菜师傅  者时就是分布式  

连接池-->连接工厂-->redisTemplate


TOPIC有一个有效时间  过了有效时间便不能  需要针对具体的业务来使用

url name password 


什么集群(cluster) ?
		
		集群时一群相互独立 但通过高速网络互相连接的计算机 ,他们构成了一个组,并以
单一系统的模式加以管理,一个客户与集群互相作用时 ,集群像是一个独立的服务器
集群配置是用于提高可用性 和 可缩放性;



集群 和 分布式 之间的区别

分布式:炒菜师傅  和  配菜 师傅  两个师傅有不同的任务  一个业务拆分成多个模块 节点 部署再不同的服务器上

集群: 炒菜师傅  炒菜师傅   两个师傅具有相同的 任务; 一个相同的业务 部署再多个服务器上  通过负载均衡
关系型数据库的四大特性 :

原子性: 你可能会像 要是数据操作中途发生 错误 出现异常怎么办 之前以及传输的数据怎么办  还没有传输完的数据怎么办  
		因为关系型数据库的特性之一  原子性  你就不需要考虑这些特性   它里面又句话就这么说的  当一组事务发生
		要么全都失败  要么全度成功   所以 当数据中途传输 发生异常  就会回滚数据    而你再去看数据库时
		就会觉得你好像 进行了一次假操作  数据库什么都没变
持久性:当你对数据库  进行修改并提交后  数据就持久性的变成你修改后的数据了

一致性:写入的数据必须完全符合数据库的预设规则  再事务发生前后  数据库的完整性并没有发生破坏

隔离性(isolation):  readuncommited读未提交  readcommited读已提交  rrepeatable read 可重复读   seriallizable串行化 

mysql可重复读: a事务都去了一个数据  并对这个数据拍了个快照 数据可就定格再这  未提交 而B事务也读取了这个数据 并修改了提交
此时a事务 其实a事务还是读取到的数据;

不可重复度(虚读):就是再一个事务中两次查询获取了不一样的结果 原因是里给一个事务读数据进行了修改操作; 一个是修改的数据 

如果一个事务 两次查询操作  再别的事务修改了此数据的情况下 还是查询形同的数据  就是可重复读

可重复读的原理就是: 对当前要读取的数据  进行了一次快照 定格再了此数据

幻读:这就就正对具体的场景来对幻读进行描述     当a事务读所有的行数据发生修改时  未提交  这是 同时事务B页对这个进行了插入操作  一个是新增的数据

所以第一个事务的用户就会发现表中还有未修改的数据 

Oracle:a事务都去了一个数据 B事务修改了  A事务此时读到的就是B事务修改的数据


一般大家都对事务的四种隔离模式比较熟悉，从松到严依次是：

- 读取未提交(Read uncommitted)：处于此模式下可能会出现脏读、幻象读、不可重复读
- 读取已提交(Read committed)：处于此模式下可能会出现幻象读、不可重复读   oracle的默认隔离级别
- 可重复读(Repeatable read)：处于此模式下可能会出现幻象读   mysql的默认隔离级别
- 串行(Serialize)：不会出现幻象读

事务多的四种isolation levl
read uncommited:一个事务读取了另一个事务  未提交的数据   会发生脏读  虚度 不可重复读 
read commited:一个事务都去了另一个事务提交的数据   发生 虚度  幻读  不可重复读  此隔离级别是oracle的默认隔离级别

repeatble  read:可重复读   还是又可能出现幻读  另一个事务对数据进行了新增操作
serialize :串线化  安全性最高  但性能最低;


常说的脏读  就发生再读取未提交 隔离级别xia

不可重复读（虚读）：指一个线程中的事务读取到了另外一个线程中提交的update的数据。
幻读：指一个线程中的事务读取到了另外一个线程中提交的insert的数据。
因为oracle的隔离级别时 read commited 所以读取的都是已提交的数据   就会发生
1.关系型数据库理论 - ACID

 

 

 

ACID，是指数据库管理系统（DBMS）在写入或更新资料的过程中，为保证事务（transaction）是正确可靠的，所必须具备的四个特性：原子性（atomicity，或称不可分割性）、一致性（consistency）、隔离性（isolation，又称独立性）、持久性（durability）。

 

A – Atomicity – 原子性

 

一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有被执行过一样。

 

C – Consistency – 一致性

 

在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。

 

I – Isolation – 隔离性

 

数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。

 
拦截器  和 过滤器的区别 

过滤器属于servlet  拦截所有   通过方法回调   
拦截器:struts  拦截访问action  通过反射

D – Durability – 持久性

 

事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。



 

关系型数据库严格遵循ACID理论。但当数据库要开始满足横向扩展、高可用、模式自由等需求时，需要对ACID理论进行取舍，不能严格遵循ACID。以CAP理论和BASE理论为基础的NoSQL数据库开始出现。

  alert(stmp.substring(1,5))//从第2个字符开始，到第5个字符；返回"cinn"
      alert(stmp.substr(1,5));//从第2个字符开始，截取5个字符；返回"cinn."

			return data.substr(10);  从第一位开始 截取10个字符
 
函数:concat（）

功能：将两个数组连接在一起；

例子：arr1=[1,2,3,4]

　　arr2=[5,6,7,8]

　　alert(arr1.concat(arr2))  //结果为[1,2,3,4,5,6,7,8]

2.函数：join()

功能：使用您选择的分隔符将一个数组合并为一个字符串

例子： var delimitedString=myArray.join(delimiter);

var myList=new Array(”jpg”,”bmp”,”gif”,”ico”,”png”);

var portableList=myList.join(”|”);

//结果是jpg|bmp|gif|ico|png

split()

 功能：使用一个指定的分隔符把一个字符串分割存储到数组

例子： str=”jpg|bmp|gif|ico|png”; arr=str.split(”|”);

//arr是一个包含字符值”jpg”、”bmp”、”gif”、”ico”和”png”的数组


如果两个字符串 是否引用同一个地址   
String aa = "abc";

String bb ="abc";

aa==bb;true因为s1和s2是同一个字符串常量abc的引用，是同一个对象地址，所以相同


三、常用的分布式方案

分布式应用和服务

将应用和服务进行分层和分割，然后将应用和服务模块进行分布式部署。这样做不仅可以提高并发访问能力、减少数据库连接和资源消耗，还能使不同应用复用共同的服务，使业务易于扩展。
分布式静态资源

对网站的静态资源如JS、CSS、图片等资源进行分布式部署可以减轻应用服务器的负载压力，提高访问速度。
分布式数据和存储

大型网站常常需要处理海量数据，单台计算机往往无法提供足够的内存空间，可以对这些数据进行分布式存储。
分布式计算

随着计算技术的发展，有些应用需要非常巨大的计算能力才能完成，如果采用集中式计算，需要耗费相当长的时间来完成。分布式计算将该应用分解成许多小的部分，分配给多台计算机进行处理。这样可以节约整体计算时间，大大提高计算效率。


四、分布式与集群

分布式（distributed）是指在多台不同的服务器中部署不同的服务模块，通过远程调用协同工作，对外提供服务。

集群（cluster）是指在多台不同的服务器中部署相同应用或服务模块，构成一个集群，通过负载均衡设备对外提供服务。


为什么在webService传输中  需要将数据序列化 反序列化?

	webService 是 基于http协议 进行数据传输的   这就需要将我们的数据序列化 都转化未字节流    来进行操作 服务器返回的数据 再反
序列化 成对象   在内存中我们可以存放对象   不需要实现序列化接口  并对此进行修改操作  但下次操作时  内存中就诶有数据  需要重新创建

这样很麻烦  如何将数据保存在 硬盘上 持久化它的生命周期呢  

			只需要实现序列化的接口即可 进行保存即可 就能以字节流输出的方式 保存到硬盘上
 手动序列化  自动序列化


当你发送数据和接收数据都是通过byte[]来获取的时候.如果你要发送对象.需要进行序列化. 如果你用WEBSERVICE来传输..则不需要因为WEBSERVICE会把数据序列化成XML数据.XML转换为byte IIS来做.所以你不需要去关心序列化的问题. 
如果你使用SOCKET那你必须进行序列化.


序列化就是将一个对象的状态（各个属性量）保存起来，然后在适当的时候再获得。
序列化分为两大部分：序列化和反序列化。序列化是这个过程的第一部分，将数据分解成字节流，以便存储在文件中或在网络上传输。反序列化就是打开字节流并重构对象。对象序列化不仅要将基本数据类型转换成字节表示，有时还要恢复数据。恢复数据要求有恢复数据的对象实例。

啊？序列化？应该是说一个数据结构，比如二叉树之类，序列化以后会变成一个char数组或者一个string字符串这样，方便你存到文件里面或者通过网络传输。然后要恢复的时候就是“反序列化”，把文件里读出来/从网络收到的char数组或者string恢复成一棵二叉树或者其他什么东西。

有抽象数据结构的数据怎么传输呢，比如二叉树，它数据有什么枝节点叶子节点，和数组不同它不是线性的。好了，在tcp协议传输数据的时候，把网络看作一个“流”（类似管道），数据从一边流进去从另一边流出来，但是二叉树要塞到这个“流”里面怎么塞……只能把它变成数组类似的东西，到了另一边再恢复成二叉树，就像运输床的时候要先拆开，到了目的地再把床头啊床板啊什么的装回去

计算机的底层都是又 01 01 01 的二进制组成的

所以当我们将类序列化存储在本地   实际上就是一个二进制文件呢  只不过我们通过一般的图形化窗口 或者 编辑器 看到的

就是解释后的高级文本来展现罢了   就算用记事本打开一张图片，依然可以看到一堆文本啊，这不过图片的二进制和记事本（编辑器）的解释器不匹配，所以看起来是乱码；但是这些都是抽象出来的，并不是说我们在浏览器看到的res就是http收到的数据，只能说这是经过浏览器处理解析后的可视化数据，本质上通过http传输的，或者说通过tcp，或者说通过光缆/无线电波传输的信息都是二进制的形式，具体在哪一层如何界定，这个真不容易量化和界定。

HTTP 是基于tcp的一种上层实现

	底层肯定是通过二进制  来进行数据传输 
	因为网线 和 光缆 都只能传输脉冲二进制

TCP/IP HTTP的区别

就好比包装员 和 快递员   http只服装包装数据  不如url 请求头 请求提 返回数据的 响应头 响应提 

tcp/ip  主要解决的是包装号的数据 如何在网络中传输 

如果只使用tcp/ip协议进行数据传输?
	传输的数据  无法被应用层识别  传输就变得毫无意义

卡车  货物  高速公路   高速公路出口

它们却有一个显著的不同：TCP提供有保证的数据传输，而UDP不提供。这意味着TCP有一个特殊的机制来确保数据安全的不出错的从一个端点传到另一个端点，而UDP不提供任何这样的保证。

 
 HTTP(超文本传输协议)是利用TCP在两台电脑(通常是Web服务器和客户端)之间传输信息的协议。客户端使用Web浏览器发起HTTP请求给Web服务器，


cookie(wangjing)   session(接口 ) ; 服务端创建   session 依赖与cookie    seesionid 
访问js cs  会不会创建session  不会 

servlet    不一定创建 session 

访问jsp   内置对象seesion  

创建session了会创建cookie码 ?
 会  依赖关系

客户端禁止cookie ?

 url重写


js 
异补变同步
async设为 false

asyncBoolean(默认: true) 默认设置下，所有请求均为异步请求。如果需要发送同步请求，请将此选项设置为 false。注意，同步请求将锁住浏览器，用户其它操作必须等待请求完成才可以执行。

	
谈谈document.ready和window.onload的区别
 window.onload必须等到页面内包括图片的所有元素加载完毕后才能执行。 
        $(document).ready()是DOM结构绘制完毕后就执行，不必等到加载完毕。
所以当我帮分别用两种方式来弹出一个提示时 会发现 $(document).ready要优先于windows.onload

而且window.onload不能编写多个    $(document).ready()可以同时编写多个

   window.onload不能同时编写多个，如果有多个window.onload方法，只会执行一个 
         $(document).ready()可以同时编写多个，并且都可以得到执行 

noseession 的原因细说?
懒加载  导致的错误
因为懒加载获取数据是通过get方式去获取数据

而因为事务的管理  当获取数据之后就将session关闭

所以出现nosession问题

处理方式
1.使用spring提供的延时加载器
2.将懒加载 修改为立即加载  hiberate中加上注解
能否将  放在spring struts前端控制器之后

不能 应该放在之前 
debug warning info 

开发:debug

项目上线:info warning 

真实开发中 应该从wsdl获取封装类的数据 
什么意思呢  就是从wsdl读取相关封装类的数据 自行创建



page<T>  只有get方法 没有set方法

可以生产 xml   json 
                                                                                     

创建一个自己的过滤器  去继承struts核心过滤器

dofilter(){
	
		//判断请求地址里面又services   就是对于的servlet
			直接放行
		//如果没有就执行的struts 的操作
			执行父类的拦截操作
		//青砖request
		getServletPath
		if(temp.startWith('/servies"'))
			chain.
		else{
			//如果没有就执行父类的操作
				super.dofilter()
			}
		
}

struts框架的入口过滤器将 cxf基于此服务器的

解决struts拦截器  拦截cxf服务的第二种方法

	创建一个过滤器继承struts的核心过滤器
	重写里面的dofileter法国法 获取访问servlet的路径
	判断是否含有/services/的路径  含有就放行
	如果没有  就执行父类的操作

然后重新配置struts2的拦截器: 
<filter> 
<filter-name>struts</filter-name> 
<filter-class>com.filter.ExtendStrutsFilter</filter-class> 
</filter> 

alt shift a 


1.日期： 

@Temporal(TemporalType.DATE) 
@Column(name = "createDate", nullable = false, length = 10) 
public Date getCreateDate() { 
  return createDate; 
} 

在页面端取值：2011-04-12 

2.时间： 

@Temporal(TemporalType.TIME) 

在页面端取值：22:50:30 

3.日期和时间(默认)： 

@Temporal(TemporalType.TIMESTAMP) 
在页面端取值：2011-04-12 22:51:34.0 

servlet 什么时候启动

默认  第一次访问创建servlet  配置启动优先顺序  可以在服务器启动时加载
单列的    init  destory 

  服务器一访问的时候

session 生命周期  默认是一个会话  序列化 反序列化 

序列化： 将数据结构或对象转换成二进制串的过程
反序列化：将在序列化过程中所生成的二进制串转换成数据结构或者对象的过程
session有时候被存储在本地 这就是一个序列化的过程

当访问服务 需要携带着它 就反序列化  二进制转化成数据结构  进行网络传输

创建一个对象的几种方法 


new 

clzz.newInstance

clone实现cloneable接口

 * 1. 使用new创建对象
 */
Book book1 = new Book();
book1.setName("Redis");
book1.setAuthors(Arrays.asList("Eric", "John"));
book1.setPrice(59.00f);
book1.setIsbn("ABBBB-QQ677868686-HSDKHFKHKH-2324234");
System.out.println(book1);
 
/**
 * 2. 使用clone创建对象
 */
try {
  Book book2 = (Book) book1.clone();
  System.out.println(book2);
} catch (CloneNotSupportedException e) {
  // TODO Auto-generated catch block
  e.printStackTrace();
}

使用Contructor.newInstance()
	clazz.newInstance(0)
 5. 使用反序列化
 */
try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("book.dat"));
    ObjectInputStream ois = new ObjectInputStream(new FileInputStream("book.dat"));) {
  oos.writeObject(book1);
 
  Book book5 = (Book) ois.readObject();
  System.out.println(book5);
 
} catch (IOException | ClassNotFoundException e) {
  // TODO Auto-generated catch block
  e.printStackTrace();
}

assm 拼接字节码 生成一个对象  加载到内存中 chlib 

反序列化 从硬盘上读取  writeoutputobject  创建对象

final:
属性:不能变化 

类:不能继承 

方法:不能重写 

 finaly  关闭资源   清理无用对象   最终的遗言 
system GC  不一定调用了 就回收垃圾   得看它

GC只能回收可控制对象  如果调用到C++的方法 就不行

如:gui 图形界面  调用的window底层组件  GC就回收不了 怎么办 手动调用

JVM 加载字节码文件的加载器

根加载器:boorstrp class loader  lib 下
 
扩展类加载器  extend   jre   ext  springjar包

应用类加载器 application  classpath 

委托机制

从上之下

层层委托

看是否属于自己的加载范围

 
自定义类加载器  
   
因为设置了 路由功能 会根据不同的路径名 去找 

而现在我们要做的效果就是  点击图片标题 会根据不同的id
去显示商品的详情

所以  需要在路径上去拼接上 id 并将这个id的只传进去 

templateUrl: 直接去访问action  action 判断是否有该静态页面

  有的化就直接去这个页面  没有就创建一个


promotion_showDetail  











 