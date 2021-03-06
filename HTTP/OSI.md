## OSI模型（Open System Interconnection Reference Model）
具体层次划分：
* 第7层应用层（Application Layer）。提供为应用软件而设的界面，以设置与另一应用软件之间的通信。例如：HTTP，HTTPS，FTP，TELNET，SSH，SMTP，POP3等。
* 第6层表达层（Presentation Layer）。把数据转换为能与接收者的系统格式兼容并适合传输的格式。
* 第5层会话层（Session Layer）。负责在数据传输中设置和维护电脑网络中两台电脑之间的通信连接。
* 第4层传输层（Transport Layer）。把传输表头（TH）加至数据以形成数据包。传输表头包含了所使用的协议等发送信息。例如：传输控制协议义（TCP）等。
* 第3层网络层（Network Layer）。决定数据的路径选择和转寄，将网络表头（NH）加至数据包，以形成分组。网络表头包含了网络数据。例如：互联网协议（IP）等。
* 第2层数据链路层（Data Link Layer）。负责网络寻址、错误侦测和改错。当表头和表尾被加至数据包时，会形成了帧。数据链表头（DLH）是包含了物理地址和错误侦测及改错的方法。数据链表尾（DLT）是一串指示数据包末端的字符串。例如以太网、无线局域网（Wi-Fi）和通用分组无线服务（GPRS）等。
* 第1层物理层（Physical Layer）。在局部局域网上传送帧，它负责管理电脑通信设备和网络媒体之间的互通。包括了针脚、电压、线缆规范、集线器、中继器、网卡、主机适配器等。

OSI 整个模型层次大致可以分为3个主要层面来看：
* 主机（高层）：应用、表示、会话。负责主机之间的数据传输
* 网络（中层）：传输、网络。负责网络互联
* 介质（底层）：数据链路、物理。负责介质传输

