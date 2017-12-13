 ActiveMQ 工作原理后

如何解决这些问题的呢?

防止拥堵,解决大批量并发访问问题

1、 解决服务之间耦合
2、 使用消息队列，增加系统并发处理量

当多个用户并发访问服务进行注册  就会都调用smsUtils来发送短信

这样直接将大量的数据 传输到数据库 会给数据库很大的压力  并且响应可能会卡顿

现在呢  我们只需要把发送短信的任务 交给activeMQ   r让mq 将消息传递给sms短信服务平台 


activeMQ   就是对应了一个生产者(用户)   一个消费者(消费)  一个中间站

一个消费者消费了 之后就删除掉 

多个消费者消费了 再删掉

有两种数据结构 Queue、Topic
1、 Queue 队列 ，生产者生产了一个消息，只能由一个消费者进行消费
2、 Topic 话题，生产者生产了一个消息，可以由多个消费者进行消费

但是你不知道什么时候去消费 有消费了就消费 就好比一个监听器 

调用smsUtils发短信

思考

创建生产者 生产  一个服务器

创建消费者接收  一个服务器



将两者之间的耦合  抛开


牺牲空间 换取时间 时间复杂度
将发短信 发邮件这些事情 交给ActiveMQ处理
"<h3>请点击地址激活:<a href=" + activeUrl
					+ "?activecode=" + activecode + ">速运快递邮件绑定" + activeUrl
					+ "</a></h3>", "text/html;charset=utf-8"


通过Runnable接口创建线程类 thread  Callable 
	
采用实现Runnable、Callable接口的方式创见多线程时，优势是：
线程类只是实现了Runnable接口或Callable接口，还可以继承其他类。
在这种方式下，多个线程可以共享同一个target对象，所以非常适合多个相同线程来处理同一份资源的情况，从而可以将CPU、代码和数据分开，形成清晰的模型，较好地体现了面向对象的思想。
劣势是：
编程稍微复杂，如果要访问当前线程，则必须使用Thread.currentThread()方法。
使用继承Thread类的方式创建多线程时优势是：
编写简单，如果需要访问当前线程，则无需使用Thread.currentThread()方法，直接使用this即可获得当前线程。
劣势是：
线程类已经继承了Thread类，所以不能再继承其他父类。

new新建  就绪start run运行  sleep阻塞   死亡 

sleep 和 wait 区别

	sleep抱着锁睡
	wait 释放了锁一块睡

为什么静态 不能调用实例

	因为加载时机  用静态去调用实例 实例还没有被创建

没有参加开始 和 考试为0的区别

get 和 post的区别?
   地址栏       request body 
	get不能上传文件  
	
不能访问本地


http://localhost:9002/bos_fore/customer_activeMail?telephone=13992684365&activecode=26226027504350989740647149168360
	

 用户点击发送验证码-->服务后台接到请求-->调用短信发送的服务接口

使用消息队列

	1.可以提高响应速度  
	2.可以解决高并发访问  数据库的压力

	用户点击发送验证码-->服务后台接到请求-->创建生产进程发送inxi-->创建消费进程接收信息-->调用服务

	1.接触后台跟服务之间的耦合
	2.提升速度

//搭建active的环境
//使用默认
		从消息队列连接工厂获取 根据用户名 密码 获取 连接
		ConnectionFactory connectionFactory = new ActiveMQConnectionFactory();
		//ConnectionFactory connectionFactory =  new org.apache.activemq.ActiveMQConnectionFactory(userName, password, brokerURL)
		//获取连接
		Connection connection = connectionFactory.createConnection();
		//第一个参数跟事务有关 在什么时候删除被消费的信息 如果true 所有的操作如果在同一个事务中 由事务的提交来决定 第二个参数无效
		//false  就自动删除或者
		Session session = connection.createSession(true, Session.AUTO_ACKNOWLEDGE);
		//一个消费者
		Queue queue = session.createQueue("SMS");
		
		//基于消息对象 创建一个生产者
		MessageProducer producer = session.createProducer(queue);
		//MessageConsumer messageConsumer = session.createConsumer(queue);
		for (int i = 0; i < 10; i++) {
			//字符串的方式
			String msg = "telephone"+","+"code";
			//telephone ,code 
			MapMessage mapMessage = session.createMapMessage();
			producer.send(session.createTextMessage(msg));
		}
		
		session.commit();
		
		
	}
ConnectionFactory connectionFactory = new ActiveMQConnectionFactory();
		//ConnectionFactory connectionFactory =  new org.apache.activemq.ActiveMQConnectionFactory(userName, password, brokerURL)
		//获取连接
		Connection connection = connectionFactory.createConnection();
		//第一个参数跟事务有关 在什么时候删除被消费的信息 如果true 所有的操作如果在同一个事务中 由事务的提交来决定 第二个参数无效
		//连接必须开启 
		connection.start();
		//false  就自动删除或者  不适用事务就不需要commit
		Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
		//一个消费者
		Queue queue = session.createQueue("你好 召唤师");
		
		//基于消息对象 创建一个生产者
		//MessageProducer producer = session.createProducer(queue);
		MessageConsumer messageConsumer = session.createConsumer(queue);
		
		messageConsumer.setMessageListener(new MessageListener() {
			
			@Override
			public void onMessage(Message message) {
				// TODO Auto-generated method stub
				TextMessage message2 = (TextMessage) message;
				
				try {
					System.out.println(message2.getText());
					//如何获取参数呢
					String text = message2.getText();
					String[] split = text.split(",");
					 String telephone =split[0];
					 String code =split[1];
					 System.out.println(telephone+code);
					 
				} catch (JMSException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			}
		});
		
		while(true){
			//不能让junit 激素
			
		}
		
		
	}

	1.发送验证码  
	参数 手机号+验证码

1.创建生产生产消息

	@Aautowird 
	@qual
	private jsm jms;

	jms.send()

	发送邮件