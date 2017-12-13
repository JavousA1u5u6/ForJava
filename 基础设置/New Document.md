 处理下载的乱码>..
乱码产生的原因 取和存的方式不一致
	
	ISO8859-1

filename new String(filename.getBytes(),"ISO8859-1");

设置响应类型为 excel的文件
response.setContentType("application/vnd.ms-excel");
设置响应头

 response.setHeader("Content-disposition", "attachment;filename="
                    + filename);

设置一个中间模型项目  互相依赖 就可以共享数据
