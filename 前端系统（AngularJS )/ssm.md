1.整合dao层
	对sqlSessionFactory 进行管理
使用spring和 mybatis 整合包 中的mapper扫描器对mapper接口进行扫描 生成代理对象



2.service
 spring对service的  进行事务
 让mapper对象注入到service对象中



3.controller

 使用注解处理器  映射器  适配器 来进行开发

最终handler 将使用组件扫描  在spring容器中进行注册



方法中事务的传播行为  required 表示对调用没有事务  就开启一个  对于调用的一个态度

required_new 都要开启一个新事务  

never : 调用者  必须没有事务

manytory:   必须开启事务  不然就报错

support: 调用者有事务  就用  没有  就以无事务运行

not _suppory  不管有没有  我都已无事务运行


nested:会滚点



扫描器  可能会冲突  所以需要排除不需要扫描的注解

怎么排除呢?
	就是每个扫描器 只扫描对应注解 所对应的包

	