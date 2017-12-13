11/15/2017 10:39:01 AM 
最为核心： MVVM、模块化、自动化双向数据绑定、依赖注入、内部指令、语义化标
签
开发如果使用 angular 最基本功能，只需要导入 angular.js

 AngularJS 快速入门

1、 在页面中引入 angular 的 js

2、 Angular 常用属性

MVVM  -- MVC 

M:

V:

C:

模块化

双向视图绑定


依赖注入

第一个列子 

双向数据绑定

 ng-app 在任何元素上使用

ng-controller 指定控制器

ng-model 指定模型s

ng-bing 属性绑定

更新模型 视图会自动更新

当你跟新了 模型后 视图会更新 

视图更新后 模型不会更新

第一个视图 <input type="text"> v

第二个视图 {{}}  v

模型  ng-model m

为什么两个模就没有效果 因为没有控制器;

为什么基于模块化?

	在1.3之前  可以地冠以一个全局控制器 

	1.3使用控制器 必须指定模块 
	<ng-app="" ng-controller="">

	angular.module()


如何异步获取数据 json 

页面上 的XXXX   都不会变 固定死的 如何 angularjs 的路由功能


发送验证码 记时?

$.scope 

$.http??
异步请求如何发送

$routProvider 路由提供


ng-app:angularJS入口  对该标签类的元素进行初始化

ng-controller:在当前元素范围内绑定指定的控制器

ng-model:指定当前元素与数据模型$scope中的属性绑定,如果数据类型中
没有此属性 会自动创建一个

ng-repeat:循环$.scope中的属性,

{{}}:花括号表示读取某一属性 相当于 ng-bind  属性取值

ng-bind 或者 {{属性名}} 进行属性取值 用于显示

ng-app 在任何元素上使用，代表 angular 应用作用域
ng-controller 指定控制器
ng-model 指定模型

 获取发送验证码 显示时间范围 记时?

<input type="text" id="showTime"/>

$("#showTime").val();
var Taketime =60;
function changeTime(){
				
	if(taketime==0){
		//移除时间  移除定时器
		$("#showTime").val("");
		clearInterval(j);
	}else{
		takeTime=taketime-count;
		$("#showTime").val(takeTime+"秒后结束");
	}
			}
			
var j = setInterval("changeTime()", 1000);

使用angularJS  又帮助我们怎么实现呢?
ar active =true;
$.scope.btnMsg = "发送验证码";
var second = 60;
function(){
	//使用ng-bind="btn-message"
	
if(active== false){
	return;
}

active = false;

secondInterval = serInterval(function(){
	if(second<0){
		$.scope.btnMsg = "重发验证码";
		//刷新视图
		$.scope.$digest();

	}else{

	$scope.btnMsg= second+"重写发送";
	second--;
	}
})

	

}
短信发送倒计时 
短信发送实现	


如何校验表单?

在方法一开始 定义几个变量 var ok1 =false;

双向数据绑定

这是Angular的核心思想之一，也是功能最强大的内容之一。在Angular文档中，我们看到：“在Angular网页应用中的数据绑定，是模型和视图层之间的数据自动同步。”这意味着，我们需要在表单中抓取数据，使用$('input[name=name]').val()并不是必需的。
我们在Angular中将数据和变量绑定在一起，无论是javascript也好，view也罢，只要有改变，两者皆变。
为了演示数据绑定，我们需要获取表单的input来自动填充变量formData。让我们回到应用于页面的Angular控制器中。我们在过一下$scope和$http。
$scope：控制器和视图层之间的粘合剂。基本上，变量使用$scope从我们的控制器和视图层之间传递和往来。具体详细的定义，请参见文档。
$http：Angular服务来帮助我们处理POST请求。更多信息，请参见文档。

$scope.formData = {};

现在，我们已经建立了一个formData对象。让我们用表单数据来填充它。在显示调用每个输入和获得val()之前，我们用ng-model绑定一个特殊的输入到变量。


在视图中显示错误和信息

我们将使用指令ng-show和ng-class来处理我们的视图，Angular双方括号允许我们将变量放置在我们需要的地方。
ng-show: 根据变量值是否存在来显示或隐藏元素. 文档
<!-- SHOW ERROR/SUCCESS MESSAGES -->

    <div id="messages" ng-show="message">{{ message }}</div>
ng-class: 根据变量值是否存在（或一些其他表达式）来添加或移除类. 文档


    $http.post('process.php', $scope.formData)

        .success(function(data) {

            ...

        });

angluarjs  双向数据绑定  模型和视图自动同步  当点击checkbox选中的时候  按钮变得可用

获取状态

	var flag  = $("input[type='checkbox']").prop('checked');

	if(flag){
		
			$(":submit").attr('disabledd';true);
	}else{

			$(":submit").attr('disabledd';true);
	}