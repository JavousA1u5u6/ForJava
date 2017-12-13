1.用户下载 选择下载的地址  然后将这个地址传入xxxx  

2.服务器接收到之后  输出流输出到这个地址   
var myUpload = $(element).upload({ 
        name: 'file', 
        action: '../../area_batchexport.action', 
        enctype: 'multipart/form-data', 
        params: {}, 
        autoSubmit: true, 
        onSubmit: function() {}, 
        onComplete: function() {}, 
        onSelect: function() {} 
}); 

问题1?如何获取选中后文件的全路径


手动创建一个maven项目 测试webService 

cxf-rs-spring 整合

@XmlRootElement(name = "User")

几个问题 返回的数据 response怎么转化为相对应的类型

从服务器获取数据之后 怎么处理

第一种 @Path 服务访问资源路径
如果访问 saveUser 方法 /userService/user
第二种 @Produces 生成（方法返回值） @Consumes 消费 （方法参数）
@Consumes 指定能够处理客户端传递过来数据格式
@Produces 指定能否生成哪种格式数据返回给客户端
第三种 @GET 查询 @PUT 修改 @POST 增加 @DELETE 删除

5、 客户端程序的编写
有两种做法
1） 使用 http client 工具 ，需要自己对 HTTP 协议内容进行定制和解析
2） WebClient 工具类使用 （CXF 自带）

4.7． ． JAX-RS  如何传输 JSON  格式的数据  ？
如果指定客户端要获取 json 内容
错误：Caused by: javax.ws.rs.ProcessingException: No message body writer has been found
for class cn.itcast.cxf.domain.User, ContentType: application/json
解决： 在项目引入 json 转换器

create 创建与服务器的连接  

type:发送给服务器数据形式 --- @Consumes

accept:接收服务器数据传输形式  --- @produces

采用HTTP协议哪种方式访问服务器


点击关联客户  弹出窗口 

$(function(){
	$("#button-association").click(function(){
		//获取选中的
		var rows = $("#grid").datagrid('getSelections');
		判断
		if(rows.length==1){
		//弹出窗口
		$("#customerwindow").window("open');
		//发送异步请求 查询关联客户的信息 和 未关联客户的信息 并将返回的信息显示在页面s
		$.post("../../fixedarea_findassociationcustomer.action",function(data{
			$(data).each(function(){
				var option = $("<option id="+this.id+">"+this.username+"("+this.username+")</option>")
				$("#noassociationSelect").append(option);
			});
		}))
		//查询已关联客户信息  需要通过关联的定区id去找
		rows[0].id
		$.post("../../fixedarea_findassociationcustomer.action",{"id":rows[0].id},function(data){
			
		});
	}
	});

});

5、 实现客户 关联到定区操作
实现页面 select 左右移动效果
当点击向右移动  就将左边未关联的 添加到右边