springmvc

dispatcherServlet(框架提供)
有了前端控制器  减少了 各个组件中的耦合性

handlerMapping

根据url查找handler  根据xml,注解查找handler  返回一个handler实例


handlerAdapter :不同类型的hanler  有不同的执行handler 的方式

优点:  可以扩展支持更多类型

handler处理器(model)  成员开发:业务处理  在实际的开发  页叫controller  后端控制器

handler 一定要handlerAdapter的规则去开发

handler处理后  结果是modelAndView   是springMVC的底层对象  包括model和view两个部分


viewReslover 视图解析  :  根据逻辑视图名 创建一个view对象 (真实物理地址)
获取业务数据  和 逻辑视图 并封装到 view对象里 

常用:jspView

不同类型  有不同

view 是一个接口   实现类暴扣:jstlView  freemaker   pdf......

view视图
作用:就是模型的数据  填充出来 展示给用户


四大器:  前端控制器   映射器     是适配       视图解析器

为什么创建web项目?
	因为表现成框架


流程:1.配置dispatcherServlet

	2.按照处理器适配器 开发handler
		使用什么处理器适配器?

	3.处理器映射器 
		可以有多个处理器映射器

	4.ViewResolver  --->返回给前端控制器 

为什么有这么多的视图接口?

	因为在视图层  有很多视图技术   比如一些动态页面技术:freemaker,jsp,velocity


使用xml开发  会造成配置文件拥堵
		
		
		


 

