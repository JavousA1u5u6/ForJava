11/19/2017 2:16:10 PM 
- 
1. 添加bootstrap 分页控件


页面上如何遍历数据呢?

<body ng-app ="paginationApp" ng-controller="paginationAppCtrl">

	<table>
			<tr>


			</tr>
	
	</table>

</body>


标题 状态 时间 活动范围 图片 

<img src="图片" alt="活动三">

					<div class="caption">
						<p>标题
						</p>

						<p class="text-right status"><span>状态</span></p>
						<p class="text-right grey">有效时间</p>
						<p class="text-right grey">适用范围</p>
					</div>

<div class="thumbnail">
					<img src="images/show/suyun/promotion2.png" alt="活动二">

					<div class="caption">
						<p>疯狂夏寄，速运三重惠，给利益享不停 手机支付运费返5%
						</p>

						<p class="text-right status"><span>进行中</span></p>
						<p class="text-right grey">20xx.xx.xx-20xx.xx.xx</p>
						<p class="text-right grey">中国大陆适用</p>
					</div>
				</div>


遇到小问题  struts2将webService发布的服务  拦截了

如何处理?
	修改struts拦截的路径


需要依赖promotion

新建一个crm_domain  专门用来存储实体类  让bos_man   bos_fore去依赖

http://localhost:9001/bos_management/upload/fed0f5de-8eb0-4601-b330-1e9919cfcc83.jpg


从前台往后台 传 需要传两个参数 一个 每页显示的记录数 当前页码

首次进入 默认传入页码1 

每页显示记录数4

后台接收到之后 根据这两个参数去查询数据

查询结果返回： 总记录数，当前页数据

根据返回总记录和每页记录条数，计算
总页数，根据总页数和当前页码，显示分页工具条

在工具条上，将静态数据换为动态数据，绑定点击事件

分页工具条:
上一页: 点击显示当前页 -1 的数据  绑定一个时间prev()
下一页: 点击显示当前页 +1 的数据  绑定一个时间next()
点击分页条上的页码 显示点击页码的数据: selectPage(page)  需要传入当前页码
当显示的当前页码的页码  点击不起作用   :isActivePage(page) 判断是否为当前显示页码

pagelist :将要显示的所有页码加入集合中;

分页条需要加判断  只显示两页 当点击第2页显示  23页:
 只显示4页
begin = currpage-5; 

if(begin<1){
	begin =1;
}

end = begin+9;

if(end > topage){
	end = total;
}

begin = end -9 ;

if(begin <1){
	begin =1 ;
}

for(var i = end;i<end;i++){
	$scope.pagelist.push(i);
}


真实开发 js 与页面分离

只能运行执行代码 不能运行对象

== "" && equal (null);


在主页面引入JS

bosfore_app.controller('ctrlRead',function($scope,$http){
	
	//定义总记录数
	$scope.totalSize =0; 
	//定义总的页数
	$scope.totalpage = 0;
	//定义当前页码
	$scope.currpage = 1;
	//定义每页的记录数
	$scope.pageSize = 5;

	//页面上定义了 prev()上一页  next()下一页   selectePage(Page)  pagelist 遍历页码 

	$scope.prev = function(){
			//必须大于1
			if($scope.currpage>1)
			$scope.selectPage($scope.currpage-1);
		} 

	$scope.next = function(){
			//必须小于总的页码
			if($scope.currpage < $scope.totalPage){
				$scope.selepage($scope.currpage +1);
			}
			
	}

	$scope.selectPage = function(page){
			//选中指定的页码后 调用$http 向后台发送数据
			$http({
				method:'get',
				url:'promotion_pageQuery.action'',
				parms:{
					'pageSize':$scope.pageSize,
					'currpage':$scope.currpage
					}

			}).success(data){
				//回调数据 返回 总的记录数  数据
				$scope.promotions = data.promotion;
				$scope.totalSize = data.totalSize;
				//根据总记录数 计算出 总的页数
				$scope.totalPage = Math.ceil($scope.totalSzie/$scope.pageSIZE);
				//当前页码 就等于当前选中的页码
				$scope.currpage = page ;

			//做出百度分页工具栏的一个效果  就只显示10页数据   

			var begin;
			var end;
			begin = $scope.currpage -5;
			if(begin<1){}
				begin=1;
			
			}
			end = begin +9;
			if(end>totalpage){
				end = totalpage
			}
			begin = end -9;

			if(begin <1){
				begin = 1;
			}
		}
		//为集合添加数据
		for(var i =begin;i<=end ;i++){

			$scope.pageList.push(i)
		}

		//

		isActive返回true时将会为此添加active央视

		//初始化时 请求第一页的数据

		$scope.selectPage($scope.currpage)

})

解决方法   获取对象就设置一个page 即可

为什么不再容器中 没有扫描 扫描到了才会注入容器中


@autoWIRED(require = true);

