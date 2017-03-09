### ��ΪSocket
Socket��Ӧ�ò���TCP/IPЭ����ͨ�ŵ��м��������㣬����һ��ӿڡ������ģʽ�У�Socket��ʵ����һ��**���ģʽ**�����Ѹ��ӵ�TCP/IPЭ����������Socket�ӿں��棬���û���˵��һ��򵥵Ľӿھ���ȫ������Socketȥ��֯���ݣ��Է���ָ����Э�顣

![Socketʹ��TCP����](https://github.com/SoSayHappy/Summary/blob/master/images/network%20mode.jpg)

### socket�Ļ�������
#### socket()����
#### bind()
��������Ҫ���ã�
�ͻ��˲���Ҫ��ϵͳ�Զ����䣻
#### listen()��connect()
����������listen()��
�ͻ��˵���connect()��
#### accept()
��������Ҫ���ã������µ�Socket����
�ͻ��˵ȴ���������������
#### read()��write()
#### close()

![Socketʹ��TCP����](https://github.com/SoSayHappy/Summary/blob/master/images/socket.jpg)

### java�������
#### ʹ��TCP
---
##### �ͻ���
``` java
Socket socket = new Socket("ip", �˿�);

InputStream is = socket.getInputStream();
DataInputStream dis = new DataInputStream(is);

OutputStream os = socket.getOutputStream();
DataInputStream dos = new DataOutputStream(os);
```
##### ��������
``` java
ServerSocket serverSocket = new ServerSocket(�˿�);
Socket socket = serverSocket.accept();
//��ȡ���ķ�ʽ��ͻ���һ��
```

#### ʹ��UDP
---
�ͻ��˺ͷ�������һ����
``` java
DatagramSocket socket = new DatagramSocket(�˿�);
InetAddress serverAddress = InetAddress.getbyName("ip");
//����
DatagramPackage packet = new DatagramPacket(buffer, length, host, port);
socket.send(packet);
//����
byte[] buf = new byte[1024];
DatagramPacket packet = new DatagramPacket(buf, 1024);
Socket.receive(packet);
```

�ο���
* [Socket ͨ��ԭ���ʵ��](http://blog.csdn.net/jiajia4336/article/details/8798421)
* [Github-LearningNotes](https://github.com/GeniusVJR/LearningNotes/blob/master/Part4/Network/Socket.md)
* [�ٶȰٿ�-Socket](http://baike.baidu.com/item/socket/281150)