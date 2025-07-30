# Nginx
## 简介
Nginx（发音为 "engine-x"）是一个高性能的开源 Web服务器、反向代理服务器、负载均衡器 和 HTTP缓存 工具。它由俄罗斯程序员 Igor Sysoev 开发，最初是为了解决 C10K 问题（即单机同时处理 1 万个并发连接）而设计的。由于其出色的性能、稳定性和低资源消耗，Nginx 已成为现代互联网架构的核心组件之一。

1. Web 服务器
   可以托管静态文件（HTML、CSS、JS、图片等）。

支持 HTTP/1.1、HTTP/2 和 WebSocket。

相比 Apache，Nginx 采用 事件驱动（Event-Driven） 架构，能高效处理高并发请求。

2. 反向代理（Reverse Proxy）
   接收客户端请求，并转发给后端服务器（如 Node.js、Java、Python 等应用）。

隐藏真实服务器 IP，提高安全性。

3. 负载均衡（Load Balancing）
   将流量分发到多个后端服务器，提高可用性和扩展性。

支持多种负载均衡算法：

轮询（Round Robin）

IP 哈希（IP Hash）

最少连接（Least Connections）
```
upstream backend {
server 192.168.1.1:8080;  # 后端服务器1
server 192.168.1.2:8080;  # 后端服务器2
server 192.168.1.3:8080 backup;  # 备用服务器
}

server {
listen 80;
server_name app.example.com;

    location / {
        proxy_pass http://backend;
    }
}
```