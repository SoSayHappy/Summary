#Socket

##���ʲô���⣿
�����н��̼�ͨ�ţ���qq����

##��ô�����
1. ʶ�����ˣ�ͨ����Ԫ�飨ip ��ַ��Э�飬�˿ڣ���ʶ����Ľ���
2. ��Ҫһ����̽ӿ����������ݣ�ʹ��Socket��

##��ʲô��
* �����ϵ���������ͨ��һ��˫���ͨ������ʵ�����ݵĽ�����������ӵ�һ�˳�Ϊһ�� socket��
* ��Դ��Unix�¡�һ����ļ�������������Ϊsocket ����һ��������ļ�
* socket �����Ǳ�̽ӿ� (API)���� TCP/IP �ķ�װ��TCP/IP ҲҪ�ṩ�ɹ�����Ա�����翪�����õĽӿڣ������ Socket ��̽ӿڣ�
* ͨ��Ҳ���� " �׽��� "���������� IP ��ַ�Ͷ˿ڣ���һ��ͨ�����ľ������������ʵ�ֲ�ͬ�������ͬ�����֮���ͨ�š�

##��HTTP�Ĺ�ϵ
HTTP �ǽγ����ṩ�˷�װ������ʾ���ݵľ�����ʽ; Socket �Ƿ��������ṩ������ͨ�ŵ�������

##��ô��
�����ļ�һ��������Ϊ ���� open �C> ��д write/read �C> �ر� close�� ģʽ������

##socket �Ļ�������
1. ������socket() ����
2. �󶨣�bind() ����
> ��������Ҫ���ã��ͻ��˲���Ҫ��ϵͳ�Զ����䣻
3. listen()��connect() ����
> ����������listen()���ͻ��˵���connect()��
4. accept() ����
> ��������Ҫ���ã������µ�Socket���󣻿ͻ��˵ȴ���������������
5. read()��write() ������
6. close() ����

##�ص�
1. socket �� TCP ���������ֽ����������

* �ͻ��������������һ�� SYN J
* ��������ͻ�����Ӧһ�� SYN K������ SYN J ����ȷ�� ACK J+1
* �ͻ��������������һ��ȷ�� ACK K+1

![TCP�������ֽ�������](http://images.cnblogs.com/cnblogs_com/skynet/201012/201012122157476286.png)

2. socket �� TCP ���Ĵ������ͷ��������

* ĳ��Ӧ�ý������ȵ��� close �����ر����ӣ���ʱ TCP ����һ�� FIN M��
* ��һ�˽��յ� FIN M ֮��ִ�б����رգ������ FIN ����ȷ�ϡ����Ľ���Ҳ��Ϊ�ļ����������ݸ�Ӧ�ý��̣���Ϊ FIN �Ľ�����ζ��Ӧ�ý�������Ӧ����������Ҳ���ղ����������ݣ�
* һ��ʱ��֮�󣬽��յ��ļ���������Ӧ�ý��̵��� close �ر����� socket���⵼������ TCP Ҳ����һ�� FIN N��
* ���յ���� FIN ��Դ���Ͷ� TCP ��������ȷ�ϡ�

![TCP�Ĵ������ͷ�����](http://images.cnblogs.com/cnblogs_com/skynet/201012/201012122157494693.png)


##java�������


###ʹ��TCP
---
�ͻ���

```
Socket socket = new Socket("ip", �˿�);

InputStream is = socket.getInputStream();
DataInputStream dis = new DataInputStream(is);

OutputStream os = socket.getOutputStream();
DataInputStream dos = new DataOutputStream(os);
```

��������

```
ServerSocket serverSocket = new ServerSocket(�˿�);
Socket socket = serverSocket.accept();
//��ȡ���ķ�ʽ��ͻ���һ��
```

��ȡ������

```
byte[] buffer = new byte[1024]; 
do{ 
	int count = is.read(buffer); 
	if(count <= 0){ break; }
	else{ 
	// ��buffer���������Щ�������� 
		} 
	}
while(true);


```


ʹ��UDP
---
�ͻ��˺ͷ�������һ����

```
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