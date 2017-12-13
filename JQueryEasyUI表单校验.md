form表单


vaildatebox验证框


require="true";

data-options="require:true"


数字验证框  class = " easy-numberbox" 继承于vaildatebox  可以说 require

precision 显示小数的位数 默认  0


**fore表单对应的action为什么要加../**
	http:localhost:8080/bos_management/pages/base/standard.html
	之前写的是 ${pageContext.request.contextPath}===bos_management
	/bos_management/
	../../standard_save.action

提交之前form中所有的表单对象都是通过校验的



**问题1:校验手机号  **

1. 1[3,4,5,7,8,9]
