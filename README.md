# socket

server:
先创建一个socket，用socket函数
调用bind函数，绑定服务端的ip和port
调用listen函数，监听当前的socket套接字，listen中的backlog参数，为理解backlog这个参数，我们必须认识到内核为任何一个给定的监听套接字维护2个队列，
1. 未完成链接队列，每个这样的SYN分节对应其中一项:已由某个客户发出并到达服务器，而服务器正在等待完成相应的TCP三次握手，这些套接字处于SYN_RCVD的状态。
2. 已完成链接队列，每个已完成的TCP三次握手过程的客户对应的其中一项，这些套接字处于ESTABLISHED状态。
而backlog=未链接队列个数+已完成链接队列个数，一般设为5
监听完之后，用accept来连接客户端的socket，
收发数据，用函数send,recv,read,write
关闭与客户端的连接套接字，既accept返回的套接字
关闭套接字，既socket返回的套接字

client:
先创建一个socket,用socket函数
连接服务端，用connect函数连接
收发数据，用函数send,recv,read,write
关闭套接字，既socket返回的套接字
