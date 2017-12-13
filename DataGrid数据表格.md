json数据的获取必须基于服务器去获取


底层自动发送 $,post  一级需要携带的参数 page(当前页的页码) .rows(每页需要的记录条数)


需要服务器返送的数据格式

json{

	名字必须定  不能改变
	"total":xx,

	"row":

	
	

}

url ;"../../querAllByPage.action";
后台

使用属性驱动接受数据

private integer page;

private integer rows;

提供set()


调取业务层 --> dao  使用

dao层使用springdata提供了pagingAndSortRepository

需要接受一个pageable 的参数

pageable p = new pagerequest(page,rows);

public PageRequest(page,rows)


会返回数据

pageData

如何封装数据为前台需要的jsonne 

使用 map

Map<String,Object> map = new hashMap<String ,Object>();

map.put("total",xx);

map.put("rows",xx);

判断栈顶是不是一个map 如果不是新建一个map  如果是map 就put

servletActionContext.getRequest().setContentType("text/json,charset=utf-8");

使用struts的插件 将值栈顶部的数据返回并转化为json

 parent maven install 

	compile 


小问题: pageRequest的page页码时从0开始

json:tkrtupjuy;i8dfmkp
{
	"total":100,
	"rows":[
		{"id":1,"name":"冰箱","price":200},
		{"id":2,"name":"冰箱","price":200},
		{"id":3,"name":"冰箱","price":200}
	]
	
}

// 属性驱动
	private int page;
	private int rows;

	public void setPage(int page) {
		this.page = page;
	}

	public void setRows(int rows) {
		this.rows = rows;
	}

	/*// 分页列表查询
	@Action(value = "standard_pageQuery", results = { @Result(name = "success", type = "json") })
	public String pageQuery() {
		// 调用业务层 ，查询数据结果
		Pageable pageable = new PageRequest(page - 1, rows);
		Page<Standard> pageData = standardService.findPageData(pageable);

		// 返回客户端数据 需要 total 和 rows
		Map<String, Object> result = new HashMap<String, Object>();
		result.put("total", pageData.getNumberOfElements());
		result.put("rows", pageData.getContent());

		// 将map转换为json数据返回 ，使用struts2-json-plugin 插件
		ActionContext.getContext().getValueStack().push(result);

		return SUCCESS;
	}*/


使用springdata 为我们提供的专注于分页的接口

里面有一个api是用于分页  findAll(Pageable,Pageable)

需要传入一个参数
Pageable
查询源码 发现 Pageable是一个接口 他有一个子实现类AbstractPageRequest

创建它只需要两个属性 page size  此size等于rows

需要注意的是 数据库中的表都是从o 开始的 
所以需要将页码-1


想办法将获取的数据传回去  需要total  rows;


修改操作
点击修改 弹出一个window框

这时需要判断 如果选择了多个选项
应该 弹出警示框 不能都选
如果只选择了一个
应该获取被选中的rows的数据 回显到window中
回显数据

getSelections

var rows =   $("#grid").('getSelections');

// 获取当前datagrid选中数据 
					var rows = $("#grid").datagrid('getSelections');
					if(rows.length != 1){
						// 没选 或 多选 
						$.messager.alert("提示信息","修改数据时，只能选中一行","warning");
					}else{
						// 只选中一行 
						var row = rows[0]; 
						// 进行表单回显操作 
						$("#standardForm").form('load',row);
						// 显示窗口
						$("#standardWindow").window('open')


注意事项 删除应该是通过id 去删除 所以应该为这个数据表格中添加一个隐藏的id数据

此修改数据在表单中 应该通过修改的表单中创建一个  <input type ="hidden" ,name = "id">


在点击保存之后  会去访问save方法   数据库在保存时  发现表中已有id就会将之前的数据覆盖掉

1 [3,4,5,7,8,9] 9????  通过jQueryEasyUI来验证手机号码是否输入正确
必须时数字
1必须11位 第二位必须是
需要做一个点我校验手机号  弹出 窗口  在这个窗口中 有一个input 
自定义NUmberbox

$.extend($.fn.validatebox.defaults.rules, {    
    minLength: {    
        validator: function(value, param){    
          	  value.length=11;
				if(value)
        },    
        message: 'Please enter at least {0} characters.'   
    }    
}); 