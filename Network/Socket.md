### 何为Socket
Socket是应用层与TCP/IP协议族通信的中间软件抽象层，它是一组接口。在设计模式中，Socket其实就是一个**外观模式**，它把复杂的TCP/IP协议族隐藏在Socket接口后面，对用户来说，一组简单的接口就是全部，让Socket去组织数据，以符合指定的协议。

![Socket使用TCP连接](https://github.com/SoSayHappy/Summary/blob/master/images/network%20mode.jpg)

### socket的基本操作
#### socket()创建
#### bind()
服务器需要调用；
客户端不需要，系统自动分配；
#### listen()、connect()
服务器调用listen()；
客户端调用connect()；
#### accept()
服务器需要调用，生成新的Socket对象；
客户端等待服务器接受请求；
#### read()、write()
#### close()

![Socket使用TCP连接](https://github.com/SoSayHappy/Summary/blob/master/images/socket.jpg)

### java代码举例
#### 使用TCP
---
##### 客户端
``` java
Socket socket = new Socket("ip", 端口);

InputStream is = socket.getInputStream();
DataInputStream dis = new DataInputStream(is);

OutputStream os = socket.getOutputStream();
DataInputStream dos = new DataOutputStream(os);
```
##### 服务器端
``` java
ServerSocket serverSocket = new ServerSocket(端口);
Socket socket = serverSocket.accept();
//获取流的方式与客户端一样
```

#### 使用UDP
---
客户端和服务器端一样的
``` java
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