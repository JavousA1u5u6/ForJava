并不是所有 LBS 云服务 都可以使用 js Ajax 访问，涉及跨域问题 （Jsonp 方式解决）

No ‘Access-Control-Allow-Origin’ 错误，跨域请求错误
当前域名 http://127.0.0.1:8020 访问域名 http://api.map.baidu.com:80

Jsonp 解决跨域问题原理，在页面生成<script> 加载远程 js 代码片段
$.getJSON("http://api.map.baidu.com/geosearch/v3/nearby?ak=zbLsuDDL4CS2U0M4KezOZZbGU
Y9iWtVf&geotable_id=153944&q=酒店
&location=116.395884,39.932154&radius=5000&callback=?",function(data){
console.log(data);
});


为什么要对数据进行编码?

	不认识中文  计算机传输  怎么办呢 ?   

期望把西安识别的码  比如转成asiciima  具体   一个支付 jdk unicode4  uf-8 8  一个字符对应8个二进制位


url编码

 1011 0011
	%B  3

编码 解码

使用场所:http请求协议中  浏览器会自动的将特殊字符转为url编码

cookie:存储中文数据时需要使用url编码对数据进行转码  默认不支持存储

js:API    encodeURICompomemt编码   decodeURICompomemt解码

Java:  URLEncoder:
		URLDecoder:




 js function golabal  


获取详细地址对应的省市区?

  百度API提供的云地理编码  可以得到更为准确的坐标信息

	
获取详细地址的信息  省市区 信息 

 	/ 选中详细地址后，调用百度地图获取 云地理

			然后将返回数据的信息 添加到省市区的选中框中

鼠标点击下拉边后的事件
var address = encodeURIComponent(myValue);
		$.getJSON(
			"http://api.map.baidu.com/cloudgc/v1?ak=zbLsuDDL4CS2U0M4KezOZZbGUY9iWtVf&address="+address+"&callback=?",
			function(data){
			if(data.status == 0 && data.result.length>0 ){
				$('#sendAreaInfo').citypicker('reset');
				$('#sendAreaInfo').citypicker('destroy');
					
				$('#sendAreaInfo').citypicker({
					province: data.result[0].address_components.province ,
					city: data.result[0].address_components.city ,
					district: data.result[0].address_components.district ,
				});
			}
		});

云地理编码 获取地点详细信息（省市区、坐标 ）

等于说现在要做的效果就是鼠标下拉选中后啷个框都要有数据  将lbs云的数据也要加载到数据中方




1.基于百度提供的city-piker 完成省市区三级联动 
导包-->根据文档
只需用 再html中引入这个便可以轻松实现 默认引入样式

style="position: relative;   
作用是将 下拉框 相对于这个dive的位置

<div "><!-- container -->
  <input readonly type="text" data-toggle="city-picker" placeholder="请选择省/市" data-level="city" >
</div>

注意的是 怎么自定义

$("#city-picker2").citypicker({
  province: "江苏省",
  city: "常州市",
  district: "溧阳市"
});


2.根据详细地址 

当点击按钮 将 数据进行更改


使用百度地图提供的api 实现输入地址 自动补全
lbs云服务 lbs云检索
提供的


jsonp是英文json with padding的缩写。它允许在服务器端生成script tags至返回至客户端，也就是动态生成javascript标签，通过javascript callback的形式实现数据读取

其实就是再服务端 生成了一个<script/> 进行远程调用  callback实现数据读取

jQuery22408246317202325746_1511434821646 && jQuery22408246317202325746_1511434821646({"status":0,"message":"ok","result":
[{"source":"baidu","location":{"lat":38.63382260639246,"lng":106.0733387934918},"bound":"38.628173,106.070200;38.636313,106.079914","formatted_address":"宁夏回族自治区银川市西夏区","address_components":{"province":"宁夏回族自治区","city":"银川市","district":"西夏区","street":"","level":"UNKNOWN"},"precise":0.4}]})

Request URL:http://api.map.baidu.com/cloudgc/v1?ak=zbLsuDDL4CS2U0M4KezOZZbGUY9iWtVf&address=%E9%93%B6%E5%B7%9D%E5%B8%82%E8%A5%BF%E5%A4%8F%E5%8C%BA%E9%95%87%E5%8C%97%E5%A0%A1%E8%A5%BF%E9%83%A8%E5%BD%B1%E8%A7%86%E5%9F%8E&callback=jQuery22408246317202325746_1511434821646&_=1511434821647

var address = encodeURIComponent(myValue); 进行了编码

encodeURIComponent() 函数可把字符串作为 URI 组件进行编码。

URIstring 的副本，其中的某些字符将被十六进制的转义序列进行替换。

首先解释下 encodeURIComponent 的作用：将文本字符串编码为一个有效的统一资源标识符 (URI)

%e9  1111  1001 
		e	9

现在的需求是将参数 加入url 进行传递 发送到服务端

但会出现问题

encodeURIComponent() 能编码"; / ? : @ & = + $ , #"这些特殊字符。对应的解码函数是decodeURIComponent()。
假如要传递带&符号的网址，所以用encodeURIComponent()

首先解释下 encodeURIComponent 的作用：将文本字符串编码为一个有效的统一资源标识符 (URI)。
为什么要用这个是因为我想把 username 整个当做参数传递给 CGI, 而不让 CGI 将 username 分割掉。这话听不明白的话我换种方式来说，如果 username = 'a&foo=boo' 而不用 encodeURIComponent 的话，整个参数就成了 name=a&foo=boo, 这样 CGI 就获得两个参数 name 和 foo. 这不是我们想要的。
Javascript 里还有个同样功能的函数 encodeURI, 但是此方法不会对下列字符进行编码：":"、"/"、";" 和 "?"。


1.用户提交订单

sendName:王五
sendMobile:13312345678
sendCompany:顺丰快递
sendAreaInfo:陕西省/西安市/未央区
sendAddress:西安市未央区草滩六路与尚苑路交叉口
recName:刘柱明
recMobile:18706848136
recCompany:顺丰快递
recAreaInfo:陕西省/汉中市/西乡县
recAddress:汉中市西乡县东兴花园
goodsType:文件
weight:20kg
remark:收好拿好不要丢
sendProNum:速运当日
payTypeNum:寄付日结
sendMobileMsg:你最棒

获取参数 数据 需要进行封装  因为 涉及到两张表的数据

订单表 与 区域biao  一对一的关系

一个订单对应  一个地址所属的区域信息

