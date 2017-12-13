给客户  让客户去编辑

kindeditor


uploadjson


filemanagerjson


allowfileManager

uploadJson

指定上传文件的服务器端程序。

数据类型: String
默认值: basePath + ‘php/upload_json.php’
fileManagerJson

指定浏览远程图片的服务器端程序。

数据类型: String
默认值: basePath + ‘php/file_manager_json.php’

// JSP
KindEditor.ready(function(K) {
        K.create('#textarea_id', {
                uploadJson : '../jsp/upload_json.jsp',
                fileManagerJson : '../jsp/file_manager_json.jsp',
                allowFileManager : true
        });
});

//成功时
{
        "error" : 0,
        "url" : "http://www.example.com/path/to/file.ext"
}
//失败时
{
        "error" : 1,
        "message" : "错误信息"
}

POST参数

imgFile: 文件form名称
dir: 上传类型，分别为image、flash、media、file


需要对其进行重新配置  不能使用默认的配


如何将上传的文件存储到 本地  并且下次读取时 从读取?


把文件存储在一个指定目录?


savePath  存放路径


saveurl 存放的相对路径

//生成图片名2

如何获取扩展名

保存  绝对路径
fileutil.copy(源文件,目标文件);


给客户反的是  相对路径

bos_managerment/upload



如何给用户显示  指定的页数 和 条数


点击6 就自动从6开始往后显示10条数据


kindeditor  一个在线html编辑工具  其实就是对普通的textarea 增添了许多新的功能


	通过初始化设置 可以有选择性的对这个   编辑器的功能  进行伸缩 或者 扩展


10   5 +1 +4以点击的页码为中心 


totalpage 20条
currentpage  当前显示页数

当前页面显示的就必须时 点中页码 x-5 x x+4 ;
begin  = current - 5;

if(x-5<=1){
		就只查询10条数据 
}else(x-5>1){
	从第7条数据开始
	就以7为源头 向后台发送查询就从7开始
}

1中午 调试代码 弄懂各个路径之间的问题
2.弄清   前台给后台发的参数  后台给前台烦的数据

事务的4中特性
持久
事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。
隔离性隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。
原子性  再一个事务中 进行增删改查操作时  要么全部完成 要么全部失败  发生错误直接回滚 
一致性在事务开始之前和事务结束以后，数据库的完整性没有被破坏

事务的安全级别

读未提交

读已提交(oracle)  可以读取另一个事务读取的已提交的事务

可重复读
MYSQL A事务开启了事务 拍了个快照 只要未提交 不会管  B事务修改可数据 提交

脏读 

读到了未提交的数据

oracle不可重复读

序列化
线程锁 安全性最高 

jsp servlet 9个内置对象  el表达式 都会被翻译  out对象 


过滤器 servlet 所有请求的页面  基于方法回调

拦截器  依赖于struets  拦截访问action  基于反射 

webservice 

为什么webService 可以不实现ser?

	a服务  序列化为了一个JSON   

对象通过网络传输

onjectinputstream

hession  必须实现 序列化接口  对象变成二进制传输  

doubbo   

imgfile = F:\Developing\STSWorkSpace\bos_management\target\tomcat\work\localEngine\localhost\bos_management\upload_ec38edbc_d7f4_4095_bd10_52224abbcd52_00000001.tmp

1.imgFilename-->imgFileName;
2.F:\Developing\STSWorkSpace\bos_management\src\main\webapp\upload
/bos_management/upload/






点击图片空间  显示服务器端  所有已上传图片的列表  


在action 图片空间所需要的数据格式返回

1.在上传文件时 就固定一个位置 比如 d://img/upload

tomcat d:bos_maagemant/upload


ueditor;


使用kindeditor编辑的内容 并不会提交

如何获取后 提交呢/  
在ifame操作
隐藏了原来的textarea
// 取得HTML内容
html = editor.html();

// 同步数据后可以直接取得textarea的value
editor.sync();
html = document.getElementById('editor_id').value; // 原生API
html = K('#editor_id').val(); // KindEditor Node API
html = $('#editor_id').val(); // jQuery

// 设置HTML内容
editor.html('HTML内容');

保存成功


分页展示功能

datagrid -->url:'' pageation;true;

rows  total ;

repository imp 分页的接口


返回page<>

前端需要一个json类型的数据

total  pagedata.gettotalelement

row 	pagedata.getContent


map.put("")

push


前端获取数据进行展示

formmater  :function(data,row,index){

return "<img>
}

return  value.replace('t','")

宣传图片和状态使用formaater实现

formatter : function(data,row, index){
					if(row.standard != null){
						return row.standard.name;
					}
					return "";
				}


发布时间 和 失效时间   使用修改模型类的方式回显诗句
	回显格式  yyyy-MM-dd   $scope.xxx = ""

totalpage 20条
currentpage 15  当前显示页数


begin = curr - 5 ;
//首先判断起始页是否小于第一页
if(begin<1){

	如果小于的化 begin=1;
}

end = curr+4;
//如果
if(end>total){
	end=toal;
	begin=end-9;
}

宣传活动任务前台分页展示

动态展示


ng-class ="{'active':true}"

前台组转好参数 发送到后台

后台接收到参数  创建wabservice连接

get数据   返回一个 page对象

封装成一个 map   totalsize 

content

页面获取到数据

将总的total闯入 pagelist中

传入之前进行一次判断

需要获得当前的页码

根据判断将









/bos_management/uploadf3c1e7f8-745e-4c2a-b5c1-93296a0967a1.jpg

为什么描述里没有讯息


public class TimeTest {

    public static void main(String[] args) {

        String s1 = "20151117190936";
        String s2="20090915-17:20:12";
        try {
//				先以它的格式解析湖区时间对象
            Date date1 = new SimpleDateFormat("yyyyMMddHHmmss").parse(s1);
            //输出格式
            System.out.println("=======解析字符串1======");
再用指定的方式  将时间对象 格式化
            System.out.println(new SimpleDateFormat("yyyy/MM/dd HH:mm:ss").format(date1));
            System.out.println(new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(date1));
            System.out.println("=======解析字符串2======");
            Date date2 = new SimpleDateFormat("yyyyMMdd-HH:mm:ss").parse(s2);
            System.out.println(new SimpleDateFormat("yyyy/MM/dd HH:mm:ss").format(date2));
            System.out.println(new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(date2));
        } catch (ParseException e) {
            e.printStackTrace();
        }
    }

}

对数据截取操作 

formatter:function(data,row,index){
								return data.substr(0,10);
							} 


解决问题 从第一未开始 截取了10个位数

如果只输入data.substr(10);  就只会从第10位开始往后截取