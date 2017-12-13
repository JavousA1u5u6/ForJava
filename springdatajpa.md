
hibernate 实体类 生成表结构  --- 领域 

@Temporal(Temporaltype.timestamp)  控制数据表


@ManytoMany()
@MantoMany 

@joinColumn

@JoinTable()

@Transient()写在 不要的属性 只在模型类中用



Archive subArchive

Courier快递员  standard收费标准  Vehicle车辆

Area区域  FixedArea定区 subArea分区

TakeTime   收派时间   --  快递员排班



orcale11g XE 版

	生成一个instance xe 

oracle 12 g 正式版
	生成一个instance orcl


开启事务
<tx:annotation - driven transaction - manager>


持久层架构搭建
spring + spring data jpa + jpa实现


集成spring环境

spring-context  ioc基本功能 依赖 bean . core .expression

spring - aop  依赖aspectj 


测试集成

spring - test


监听器
spring - web 

整合持久

spring -orm
2.Web.xml   配置 listener


3.src/main/resource  建立 aplicationContext.xml


4.提供外部属性文件  日志文件log4j.

spring整合jpa

config database conn :c3p0 conn 




5事务

jpaTransactionManager


Archive 档案表 onetomany  subArchive子档案表 

vehicle 喂阔   车辆


courier 阔瑞尔  快递员

area -->   subarea  fixedarea

add / remove 			begin / end				create / destroy 	
insert / delete			first / last       		get / set
increment / decrement	put / get					add / delete       
lock / unlock      		open / close				min / max
old / new				start / stop				next / previous
source / target	目标, 指标, 靶子		show / hide	人的皮肤; 皮革			send / receive
source / destination		cut / paste				up / down



一个区  有很多分区  针对每一个定区 定点有快递员

data-options="region:'north' 定义布局  东西南北

两种数据格式  一个标准  一个简单

标准使用嵌套子类节点的方式  在有大量子类的时候  定义很不方便
<div data-options="title:'基础菜单'">
					<!-- 通过ztree 插件，制作树菜单 -->
					<ul id="baseMenu" class="ztree"></ul>
				</div>
$(function(){
				// 1、 进行ztree菜单设置 
				var setting = {
					data: {
						simpleData: {
							enable: true // 支持简单json数据格式
						}
					}
				};

// 2、提供ztree树形菜单数据 
				var zNodes = [
					{id:1,pId:0,name:"父节点一"},
					{id:2,pId:0,name:"父节点二"},
					{id:11,pId:1,name:"子节点一"},
					{id:12,pId:1,name:"子节点二"}, 
					{id:13,pId:2,name:"子节点三"},
					{id:14,pId:2,name:"子节点四"}
				];
	// 3、生成菜单
				$.fn.zTree.init($("#baseMenu"), setting, zNodes);

callback: {
						onClick : function(event, treeId, treeNode, clickFlag){
							var content = '<div style="width:100%;height:100%;overflow:hidden;">'
								+ '<iframe src="'
								+ treeNode.page
								+ '" scrolling="auto" style="width:100%;height:100%;border:0;" ></iframe></div>';							
							// 没有page树形菜单，不打开选项卡
							if(treeNode.page != undefined && treeNode.page != ""){
								// 如果选项卡已经打开，选中 
								if($("#mytabs").tabs('exists',treeNode.name)){
									// 选中选项卡
									$("#mytabs").tabs('select',treeNode.name);
								}else{
									// 如果没有打开，添加选项卡 
									$("#mytabs").tabs('add',{
										title:treeNode.name,
										content: content,
										closable :true
									});
								}
							}
						}
					}

$("#mytabs").tabs({
					onContextMenu: function(e, title,index){
						// 阻止默认菜单显示
						e.preventDefault();
						
						// 显示自定义右键菜单
						$("#mm").menu('show',{
							left : e.pageX,
							top : e.pageY
						});
					}
				});

当鼠标点击菜单中的菜单项   根据点击的选项关闭相应的窗口
1. 关闭当前  获取当前的选项卡  然后删除
2. 关闭其他	获取除当前之外的所有选项卡  删除
3. 关闭所有   获取所有选项卡 删除

为div 绑定点击事件  当点击之后获取所有的tabs  然后关闭

if(index)  获取当前选中的index 

如果index != index 


获取所有tabs下的 div   遍历 可以获取每一个div的索引


如何判断已有选项卡后就不再添加
先获取树形菜单的名字  

根据树形菜单的名字 取选项卡中查找 如果有就选中

如果没有就创建一个

根据名字获取选项卡
 var exist_tab = $("#mytabs").tabs('getTab',nodename);


if(exist_tab){
	$("#mytabs").tabs('select',nodename)
}else{
	$("#mytabs").tabs('add',{
		
		'id':'tab',
		title:noteTest,
		fit:true,
		content:'',
		closable:true

})
}

本机 127.0.0.1

不使用静态的html去加载

异步获取数据

加载菜单栏
$.post("./data/menu.json",function(data){
		$.fn.zTree.init($("#adminMenu"), setting, data);
		
},"json")


新思路
// 设置全局变量 保存当前正在右键的tabs 标题 
				var currentRightTitle  ;

根据name去删除



idetity:自增  oracle不支持 

AUTO:jpa自动选择合适的策略

sequence:通过序列 产生主键  @SequenceGenerator注解指定序列名



@Transient

请求数据库

$.post("../")

使用springdatajpa 只需要根据相应的业务需求  开发一个空的repository去继承相应的功能接口

不需要对dao接口做任何实现  
 


$("closerAll").click(function(){
	var tabs = $("#tt").tabs('tabs');
关闭所有
	$(tabs).each(function(){
		if((this).panel("options").title ! = '消息中心'){
				$("#tt").tabs('close',title);
			}

	});

})

当右击可以获得三个参数 其中就有title


也可以使用for循环

因为在tabs这个面板容器中   装了很多子面板  就可以看成一个数组


  数组的第一位是  首页 

我们需要关闭面板就需要循环去 遍历一个一个删  就从1开始