Java网络编程主要涉及以下几个方面： 1. Socket编程 Java提供了Socket和ServerSocket类来实现基于TCP协议的网络编程。Socket类用于客户端的编程，ServerSocket类则用于服务端的编程。 以下是客户端和服务端的示例代码： 客户端：

```csharp

try {
    Socket socket = new Socket("localhost", 8888);

    // 发送数据
    OutputStream out = socket.getOutputStream();
    out.write("Hello, server!".getBytes());

    // 接收数据
    InputStream in = socket.getInputStream();
    byte[] buffer = new byte[1024];
    int len = in.read(buffer);
    System.out.println(new String(buffer, 0, len));

    // 关闭连接
    in.close();
    out.close();
   .close();
} catch (IOException e) {
    e.printStackTrace();
}
```

服务端：

```go

try {
    ServerSocket serverSocket = new ServerSocket(8888);
    System.out.println("Server started...");

    Socket socket = serverSocket.accept();
    System.out.println("Client connected...");

    // 接收数据
    InputStream in = socket.getInputStream();
    byte[] buffer = new byte[1024];
    int len = in.read(buffer);
    System.out.println(new String(buffer, 0, len));

    // 发送数据
    OutputStream out = socket.getOutputStream();
    out.write("Hello, client!".getBytes());

    // 关闭连接
    in.close();
    out.close();
    socket.close();
    serverSocket.close();
} catch (IOException e) {
    e.printStackTrace();
}
```

2. URL编程 Java提供了URL和URLConnection类来实现基于HTTP协议的网络编程。URL类用于表示一个统一资源定位符，URLConnection类则用于建立与URL之间的连接。 以下是使用URLConnection获取网页内容的示例代码：

```java

try {
    URL url = new URL("https://www.baidu.com");
    URLConnection connection = url.openConnection();
    connection.connect();

    InputStream in = connection.getInputStream();
    BufferedReader reader = new BufferedReader(new InputStreamReader(in));

    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println(line);
    }

    reader.close();
    in.close();
} catch (IOException e) {
    e.printStackTrace();
}
```

3. UDP编程 Java提供了DatagramPacket和DatagramSocket类来实现基于UDP协议的网络编程。DatagramPacket类用于封装UDP数据包，DatagramSocket类则用于发送和接收UDP数据包。 以下是发送和接收UDP数据包的示例代码： 发送：

```java

try {
    DatagramSocket socket = new DatagramSocket();

    // 发送数据
    String message = "Hello, server!";
    byte[] data = message.getBytes();
    DatagramPacket packet = new DatagramPacket(data, data.length, InetAddress.getLocalHost(), 8888);
    socket.send(packet);

    // 关闭连接
    socket.close();
} catch (IOException e) {
    e.printStackTrace();
}
```

接收：

```csharp

try {
    DatagramSocket socket = new DatagramSocket(8888);

    // 接收数据
    byte[] buffer = new byte[1024];
    DatagramPacket packet = new DatagramPacket(buffer, buffer.length);
    socket.receive(packet);
    System.out.println(new String(packet.getData(), 0, packet.getLength()));

    // 关闭连接
    socket.close();
} catch (IOException e) {
    e.printStackTrace();
}
```

以上是Java网络编程的基础知识，需要了解更多的内容可以深入学习网络编程相关的知识。