
原生全文检索api  lucen 

搜素引擎服务器:/solr elasticSearch 分布式  后者性能更好  基于lucen

权限控制: Apache shiro


运单管理  查询操作 再添加运单时  为运单创建全文索引 

eleasticSearch 搜索服务器  进行搜索


字段模糊查询  涉及到一个大数据量得性能问题;

s发货地: 朝阳

select  from xxx where sendAddress like %朝阳%;

1.数据库有很多这样得数据 而like模糊查询 是无法对数据列建立索引得

就只能一条条得进行  字符串比对查询 效率非常低下

怎么办呢

面对这种大字段量得

使用java  解决方案:  建立数据得索引库

什么叫全文检索?

	全文检索 一个简单得描述 就是

什么是全文索引?

	文本信息中所有得词 进行切分  与搜索像进行比对

采用得就是分词器 : 词条-->

换个地方存储数据  从新搞了个地方(索引库)    并通过分词器 将数据进行划分

汉台区风景路

同maven rebuild index 

方便我们再pom文件中  查询

学习 ES 常见的API操作(了解):  几个query

termquery : 词条等值查询

wildCardQuery:词条模糊查询

boolQuery:组合复杂查询

queryStringquery: 将记录查询再分词 再查 结果取交集  默认取并集  需要指定方式

可能会出现查询条件不正确;

spring data elasticSearch

索引对象:存储数据的表结构  

文档:一条数据记录 存在索引对象上 joon  

文档类型:  一个索引对象可以存储多个数据类型  数据用文档类型进行标识 

映射(mapping):数据到是如何像搜索服务器存储的

词条(term):

elasticSearch   :对于中文   是一个字 一个词条  不支持中文的分词

所以后期需要


建立文档时需要正对于一个已经存在的对象 来 构建文档



# spring整合elasticSearch #

	基于spring data的API帮助我们简化操作

1.

 



	

String s1 = "";

String s2 = ""



1.运单号

2.是这个运单的唯一标识  +  条形栏
3.必须作为唯一识别
4.在未使用时就产生了  使用时只是把它激活而已

行编辑
	insert row 

	begin editor

	cancle editor 

	s

	列属性

	editor:function(){
			$("#grid").datagrid('insertRow',{
			

		)

}

js中的5中原始类型

undefinde null  ""  object  

number:整数/小数 /NAN

string:

boolean:

null:

undefined:

if(!currentEditorIndex){

	//正在编辑
	//会存在自动的类型转换
	//首先必须知道其他类型会自动转为boolean
	//存在一个数据类型转换的问题
	return:
}

o为假  非0为真

while(1)

js这种操作
大量简化逻辑判断


在js中有5大基本数据leix

number 整数/小数  NAN

string 

boolean

null 

undefine 


运单快速录入的列表展示

(ssh)

前台需要往后台发送两个参数:pageSize ,currentpage;

pagination

url:"xxx.action"
后台需要接收这两个参数

属性/模型

进行查询

spring data jpa 

pageable =  new pageRequest(page-1,rows)

sort?排序对象  可以对数据排序

构造它需要传入order-->dicription-->

如果套把新加入的数据放在最上面

怎么用?

sort sort = new order ()
page<wayBill> pagedata = findAll(apgeable)

调用方法pushValueStack(pageData);  就自动压入值栈

重新加载 方法  因为这是异步
$("#grid").datagrid('reload');


详细信息

先将货物发出去 再慢慢补录

在运单中 对 获取的一些信息  进行精准修复


1.客户使用前端 在线下单

2.客户电话下单  由工作人员在后台管理系统录入

3.可能你家附件就由一个网点 客户直接带货物到网点

integer status;


问题1
什么时候用 

1.通过client  去通过几个查询的api查询 termQuery?
			

2.使用elasticsearchTemplate?

3.使用继承了elasticsearchRepository的接口进行查询?

根据具体的业务场景需要  选择适当的 工具 去查询




问题2

为什么客户端定义了 id的数据类型是long  服务器上却显示string?


1.从前台发送数据 

2.需要将所有的运单信息存如索引库

先从数据库查询所有的运单 信息  然后将所有的运单信息存入所英库

导包


