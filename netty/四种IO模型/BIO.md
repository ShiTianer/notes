网络编程的基本模型是 Client/Server 模型，两个进程之间互相通信，服务端提供位置信息（IP和端口号），客户端向服务端监听的地址发起连接请求，通过三次握手建立连接，连接建立成功，双方就可以通过网络套接字（Socket）进行通信。

关于Socket和tpc/ip协议：

https://blog.csdn.net/github_34606293/article/details/78230456

BIO通信模型的服务端，通常由一个独立的Acceptor线程负责监听客户端的连接，它接收到客户端的连接请求之后为每个客户端创建一个新的线程进行处理，处理完成之后通过输出流返回应答给客户端，线程销毁，典型的一请求一应答通信模型。

BIO通信模型最大的问题就是缺乏弹性伸缩能力，当客户端并发访问量增加后，服务端的线程个数和客户端并发访问数呈1:1的正比关系，线程数膨胀之后，系统性能急剧下降，随着并发访问量的增大，系统会导致进程宕机或者僵死，不能对外提供服务。



