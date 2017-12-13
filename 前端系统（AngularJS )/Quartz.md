11/20/2017 3:19:36 PM 

谁在什么时间去做了什么 


定时任务

this ? do ? when?

宣传任务时有一个开始时间  和 结束时间的 

我们就系统能够自动的修改promotion表的字段

timer 定时	

阔Z  是一个开源项目   -->jobs 


jobDetail  

job工作


trigger 什么时候工作  触发

simple trigger 的使用

CornTrigger 的使用

0 0 12 ? wed 

0000*? 每个月的一日的零点

为jop 配置了一个hellojob的类全名 但它本身不再spring的容器中

那么它能注入进来码

定义了一个被spring管理的bean

向在job中注入spring管理的bean 

@autoWIRED
   hellow service
但是并没有管理这个bean

 在hellojob中没有将 service注入


结局必须 管理hellojon 管理

jobFactory  可以让指定的类被spring管理 spring自动注入的属性

注入jobFactory

spring就是一个打容器  要想使用spring注入 就必须先让对象被sprig管理


schdule 大管家  将jobdatil(job.class)  trigger 交给执行
		
		class  hellow 
		schfac
	jobfac   cronfac

	hellowjon


	helloService

只能通过犬类名 创建一个对象  但是这个对象没有被spring管理

所以 new 出来的 helloservice 本省就时null;

当没有引入jobFactory时 报了空异常 注入的 promotionService 因为

==

job需要:class对象是   现在value 给了一个全类名 反射生成一个新对象  

这个新对象并没有在我们的spring容器中   

debug expression


关于描述 中 显示图片的问题

Request URL:http://localhost:9003/bos_management/upload/bda2728d-314c-4c60-acf3-5d3b3f0e8d4f.jpg

通过这个路径 去获取图片的时  获取不到

到失效时间 自动过期

job  将宣传的状态改为2 

	proservice.updateStatus(宣传的id);


trigger

	需要获取它的失效时间 2017-11-20 -8点半
	将它的时间进行拆分
	以-进行分割
	endDate.toString.split('-');
	可以获取一个数组
	第一位就是年份endDate[0]   endDate[1]月 endDate[2]天  endDate[3]时
	endDate[4]分 endDate[5]秒
	生成一个propertu文件  动态的绑定数据  将这数据写入此文件
	引入外部的propertites文件
	设置触发器执行的属性值
	通过这些数据就可以来写我们的表达时表达式

	0 0/1 * * ?

原因就是quartz 初始化的时自己的jobcontext 不同于spring的ApplicationContext 所以无法直接注入 

2解决方法   使用 jobDateMap  来向 JobDetail 传参
wed
*标识每个 每秒 每分
/用来标识值的增量
0/15  m每隔15秒 cong 0开始
3/15 从3开始 没隔15 
3,23,43  
?没有指定值
2.  ref 直接引入一个值

0 0 12 ? * 3 每周二中午 12 点执行任务
0 0 0 0 * ? 每月 1 日 0 点执行任务
0-59
0-23
0-31

schedule










