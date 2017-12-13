
在什么时候需要去授权呢?

	每次都要查数据库  搞到内存中

第一查询 从map中获取数据
		键:id  值:权限数据集合

第二查询 

	减少了与数据库的交互 提高了性能  优化了服务器


未加缓存前:每当去访问一个需要被权限控制的资源时

就会调用realm的授权方法  根据当前用户 去查询数据库

每一次调用都会去查询


这种数据 重复的在被查询

同样作为缓存工具,为什么不用redis ?
	因为shiro默认就有对ehchche的支持,使用redis需要定制

	而且在后台管理系统  大多使用ehcache  而且新版本的 也支持对集群的控制


什么样的数据可以被缓存?

	不经常被改变的数据

为什么不自己写个map?

	
spring整合ehcache的流程?

第一步： 在 common_parent 导入 ehcache maven 坐标
Ehcache 开发包

第二步： 使用 ehcache ，导入 ehcache.xml 配置文件
解压 ehcache-core.jar 包 ，将 ehcache-failsafe.xml 复制 src/main/resources
改名 ehcache.xml  自定义缓存区

第三步： 配置 spring 整合 ehcache
将 ehcacheManager 交给 spring 管理

第四步： 配置 shiro 封装缓存管理器

第五步： 将 shiro 的缓存管理器，注入到安全管理器中

第六步： 对认证数据、授权数据 哪些进行缓存 ？
配置 Realm

注意： 使需要缓存对象，实现 Serializable 接口
java.io.NotSerializableException: cn.itcast.bos.domain.system.User



就时secruityManager 配置一个缓存区  然后将用户的授权信息 存到这个缓存中

所以在缓存配置好之后就应该注入安全管理器

获取时 就从缓存中拿




需要手动配置realm  为什么可以进行手动配置


出错:user未serializable 

	需要缓存的对象必须实现缓存接口

在问shiro怎么问?

	
用了shiro数据永不用缓存


缓存内部的实现原理


map会经常的被查询和设置值

一定会在高并发下去使用

高并发的map一定会出问题  hashmap线程不安全  链表的死循环

connections 将线程不安全的集合转成安全的  syncharMap()

底层就是为此加了一个同步的操作  每一步加了个sunchronized 锁

但是在web开发中 这是很不好的  禁止的  

高并发  排队  但这样损失性能

2.concurrentHashMap

支持完全并发的map访问  


哈希表: 单个元素
concurrentHashMap:又存的时map集合  跟哈希表就没关系


如何实现只允许10个人吃饭?

	semaphore(int number);

cyclicBarrier 

java . util.concurrent


敏捷开发


一些api的使用
@cacheable :用于查询方法,对方法返回结果进行缓存

  @cacheEvict:清除缓存去数据  用于增删改

spring整合ehcache后  缓冲注解的使用


来个小小例子

对你传递不同的参数 进行缓存

参数:数据

key = "#pageable.pageNumber"

更加细粒度去使用缓存 比如某个值 经常被使用 但是不会发生变化  


Hibernate: select count(standard0_.C_ID) as col_0_0_ from T_STANDARD standard0_
Hibernate: select * from ( select standard0_.C_ID as C_ID1_12_, standard0_.C_MAX_LENGTH as C_MAX_LENGTH2_12_, standard0_.C_MAX_WEIGHT as C_MAX_WEIGHT3_12_, standard0_.C_MIN_LENGTH as C_MIN_LENGTH4_12_, standard0_.C_MIN_WEIGHT as C_MIN_WEIGHT5_12_, standard0_.C_NAME as C_NAME6_12_, standard0_.C_OPERATING_COMPANY as C_OPERATING_COMPAN7_12_, standard0_.C_OPERATING_TIME as C_OPERATING_TIME8_12_, standard0_.C_OPERATOR as C_OPERATOR9_12_ from T_STANDARD standard0_ ) where rownum <= ?
Hibernate: select count(standard0_.C_ID) as col_0_0_ from T_STANDARD standard0_
Hibernate: select * from ( select standard0_.C_ID as C_ID1_12_, standard0_.C_MAX_LENGTH as C_MAX_LENGTH2_12_, standard0_.C_MAX_WEIGHT as C_MAX_WEIGHT3_12_, standard0_.C_MIN_LENGTH as C_MIN_LENGTH4_12_, standard0_.C_MIN_WEIGHT as C_MIN_WEIGHT5_12_, standard0_.C_NAME as C_NAME6_12_, standard0_.C_OPERATING_COMPANY as C_OPERATING_COMPAN7_12_, standard0_.C_OPERATING_TIME as C_OPERATING_TIME8_12_, standard0_.C_OPERATOR as C_OPERATOR9_12_ from T_STANDARD standard0_ ) where rownum <= ?

先查寻了  所有的记录条数
然后再从表中查询所有的数据  只取其中runnum <=  当前pagesize 的记录数
我执行啦



每次都要发送昂与的查询

现在将查询结果存储到缓冲中	

使用之后 只查询一次  之后就再也不去查呢


但是有时候  我们的数据发生改变 我们就需要将之前的缓存数据全部去掉 然后重新将拆线呢的数据加入缓存中 

再对数据增删改的操作时用  @CacheEvict 对缓存数据进行清理

当再次执行查询操作时 缓存中就没有数据呢  就会从数据库从新去查询


　什么样的数据适合存放到第二级缓存中？
　　1、很少被修改的数据
　　2、不是很重要的数据，允许出现偶尔并发的数据
　　3、不会被并发访问的数据
　　4、参考数据
　　不适合存放到第二级缓存的数据？
　　1、经常被修改的数据
　　2、财务数据，绝对不允许出现并发
　　3、与其他应用共享的数据。







