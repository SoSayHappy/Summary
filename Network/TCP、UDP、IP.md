
##TCP/IP 协议栈
TCP/IP 协议栈主要分为四层: 应用层、传输层、网络层、数据链路层, 每层都有相应的协议，如下图
![TCP/IP 协议栈](http://blog.chinaunix.net/attachment/201304/27/26833883_1367053079KNJe.png)

##TCP
TCP 协议是面向连接、保证高可靠性 (数据无丢失、数据无失序、数据无错误、数据无重复到达) 传输层协议。

###三次握手建立连接
建立连接


###四次挥手断开连接
断开连接



##UDP
UDP 协议也是传输层协议，它是无连接，不保证可靠的传输层协议。


TCP与UDP的区别
----------

<table class="table table-bordered table-striped table-condensed">
	<tr>
		<td>TCP面向<strong>有链接</strong>的通信服务</td>
		<td>UDP面向<strong>无连接</strong>的通信服务</td>
	</tr>
	<tr>
		<td>TCP提供可靠的通信传输</td>
		<td>UDP不可靠,会丢包</td>
	</tr>
	<tr>
		<td>TCP保证数据顺序</td>
		<td>UDP不保证</td>
	</tr>
	<tr>
		<td>TCP数据无边界</td>
		<td>UDP有边界</td>
	</tr>
	<tr>
		<td>TCP速度慢</td>
		<td>UDP速度快</td>
	</tr>
	<tr>
		<td>TCP面向字节流</td>
		<td>UDP面向报文</td>
	</tr>
	<tr>
		<td>TCP一对一</td>
		<td>UDP可以一对一，一对多</td>
	</tr>
	<tr>
		<td>TCP报头至少20字节</td>
		<td>UDP报头8字节</td>
	</tr>
	<tr>
		<td>TCP有流量控制，拥塞控制</td>
		<td>UDP没有</td>
	</tr>
</table>



**为什么UDP比TCP快**
 1. TCP需要三次握手
 2. TCP有拥塞控制，控制流量等机制



**为什么TCP比UDP可靠**
 1. TCP是面向有连接的，建立连接之后才发送数据；而UDP则不管对方存不存在都会发送数据。
 2. TCP有确认机制，接收端每收到一个正确包都会回应给发送端。超时或者数据包不完整的话发送端会重传。UDP没有。因此可能丢包。



**什么时候使用TCP**
当对网络通讯质量有要求的时候，比如：整个数据要准确无误的传递给对方，这往往用于一些要求可靠的应用，比如HTTP、HTTPS、FTP等传输文件的协议，POP、SMTP等邮件传输的协议。
在日常生活中，常见使用TCP协议的应用如下：
浏览器，用的HTTP
FlashFXP，用的FTP
Outlook，用的POP、SMTP
Putty，用的Telnet、SSH
QQ文件传输


**什么时候应该使用UDP：**
当对网络通讯质量要求不高的时候，要求网络通讯速度能尽量的快，这时就可以使用UDP。
比如，日常生活中，常见使用UDP协议的应用如下：
QQ语音
QQ视频
TFTP



##IP
I P 是 T C P / I P 协议族中最为核心的协议。所有的 T C P、U D P、I C M P 及 I G M P 数据都以 I P 数据报格式传输。

###特点
* 不可靠，不能保证 I P 数据报能成功地到达目的地；
* 无连接， I P 并不维护任何关于后续数据报的状态信息；