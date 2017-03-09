#Socket

##解决什么问题？
网络中进程间通信，如qq聊天

##怎么解决？
1. 识别端与端，通过三元组（ip 地址，协议，端口）标识网络的进程
2. 需要一个编程接口来交互数据，使用Socket；

##是什么？
* 网络上的两个程序通过一个双向的通信连接实现数据的交换，这个连接的一端称为一个 socket。
* 起源于Unix下“一起皆文件”概念，可以理解为socket 即是一种特殊的文件
* socket 本质是编程接口 (API)，对 TCP/IP 的封装，TCP/IP 也要提供可供程序员做网络开发所用的接口，这就是 Socket 编程接口；
* 通常也称作 " 套接字 "，用于描述 IP 地址和端口，是一个通信链的句柄，可以用来实现不同虚拟机或不同计算机之间的通信。

##和HTTP的关系
HTTP 是轿车，提供了封装或者显示数据的具体形式; Socket 是发动机，提供了网络通信的能力。

##怎么用
类似文件一样，过程为 “打开 open –> 读写 write/read –> 关闭 close” 模式来操作

##socket 的基本操作
1. 创建，socket() 函数
2. 绑定，bind() 函数
> 服务器需要调用；客户端不需要，系统自动分配；
3. listen()、connect() 函数
> 服务器调用listen()；客户端调用connect()；
4. accept() 函数
> 服务器需要调用，生成新的Socket对象；客户端等待服务器接受请求；
5. read()、write() 函数等
6. close() 函数

##重点
1. socket 中 TCP 的三次握手建立连接详解

* 客户端向服务器发送一个 SYN J
* 服务器向客户端响应一个 SYN K，并对 SYN J 进行确认 ACK J+1
* 客户端再想服务器发一个确认 ACK K+1

![TCP三次握手建立连接](http://images.cnblogs.com/cnblogs_com/skynet/201012/201012122157476286.png)

2. socket 中 TCP 的四次握手释放连接详解

* 某个应用进程首先调用 close 主动关闭连接，这时 TCP 发送一个 FIN M；
* 另一端接收到 FIN M 之后，执行被动关闭，对这个 FIN 进行确认。它的接收也作为文件结束符传递给应用进程，因为 FIN 的接收意味着应用进程在相应的连接上再也接收不到额外数据；
* 一段时间之后，接收到文件结束符的应用进程调用 close 关闭它的 socket。这导致它的 TCP 也发送一个 FIN N；
* 接收到这个 FIN 的源发送端 TCP 对它进行确认。

![TCP四次握手释放连接](http://images.cnblogs.com/cnblogs_com/skynet/201012/201012122157494693.png)


##java代码举例


###使用TCP
---
客户端

```
Socket socket = new Socket("ip", 端口);

InputStream is = socket.getInputStream();
DataInputStream dis = new DataInputStream(is);

OutputStream os = socket.getOutputStream();
DataInputStream dos = new DataOutputStream(os);
```

服务器端

```
ServerSocket serverSocket = new ServerSocket(端口);
Socket socket = serverSocket.accept();
//获取流的方式与客户端一样
```

读取输入流

```
byte[] buffer = new byte[1024]; 
do{ 
	int count = is.read(buffer); 
	if(count <= 0){ break; }
	else{ 
	// 对buffer保存或者做些其他操作 
		} 
	}
while(true);


```


使用UDP
---
客户端和服务器端一样的

```
DatagramSocket socket = new DatagramSocket(端口);
InetAddress serverAddress = InetAddress.getbyName("ip");
//发送
DatagramPackage packet = new DatagramPacket(buffer, length, host, port);
socket.send(packet);
//接收
byte[] buf = new byte[1024];
DatagramPacket packet = new DatagramPacket(buf, 1024);
Socket.receive(packet);
```

参考：
* [Socket 通信原理和实践](http://blog.csdn.net/jiajia4336/article/details/8798421)
* [Github-LearningNotes](https://github.com/GeniusVJR/LearningNotes/blob/master/Part4/Network/Socket.md)
* [百度百科-Socket](http://baike.baidu.com/item/socket/281150)