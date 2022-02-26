# 初识
- HTTP：超文本传输协议

  ![20220122165428-2022-01-22-16-54-29](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122165428-2022-01-22-16-54-29.png)
- 应用层协议，基于TCP协议
- 请求响应
- 简单可扩展
- 无状态
# 协议分析
## 发展
![20220122170221-2022-01-22-17-02-22](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122170221-2022-01-22-17-02-22.png)
## 报文
### HTTP/1.1
- requests
  - 起始行（Method Path Version）
  - handers
  - 空行
  - body
- responses
  - 起始行（Version StateCode StatusMessage）
  - handers
  - 空行
  - body
- Method
  - ![20220122170923-2022-01-22-17-09-23](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122170923-2022-01-22-17-09-23.png)
  - Safe（安全的）：不会修改服务器的数据的方法 GET HEAD OPTIONS 
  - Idempotent（幂等）：同样的请求被执行一次与连续执行多次的效果是一样的，服务器的状态也是一样的所有safe的方法都是Idempotent的 GET HEAD OPTIONS PUT DELETE
- 状态码
  - ![20220122172107-2022-01-22-17-21-07](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122172107-2022-01-22-17-21-07.png)
- RESTful API
  - RESTful API:-APlit风格；REST-Representational State Transfer
    - 每一个URI代表一种资源；
    - 客户端和服务器之间，传递这种资源的某种表现层；
    - 客户端通过HTTP method，对服务器端资源进行操作，实现"表现层状态转化"。
  - ![20220122172728-2022-01-22-17-27-29](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122172728-2022-01-22-17-27-29.png)
- 请求头
  - ![20220122173830-2022-01-22-17-38-31](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122173830-2022-01-22-17-38-31.png)
- 响应头
  - ![20220122174241-2022-01-22-17-42-42](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122174241-2022-01-22-17-42-42.png)
- 缓存
  - ![20220122174918-2022-01-22-17-49-19](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122174918-2022-01-22-17-49-19.png)
  - ![20220122175413-2022-01-22-17-54-13](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122175413-2022-01-22-17-54-13.png)
- Cookie
  - ![20220122180007-2022-01-22-18-00-08](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122180007-2022-01-22-18-00-08.png)
## HTTP/2
- 概述
  - ![20220122180533-2022-01-22-18-05-34](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122180533-2022-01-22-18-05-34.png)
  - ![20220122180836-2022-01-22-18-08-36](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122180836-2022-01-22-18-08-36.png)
  - ![20220122180850-2022-01-22-18-08-51](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122180850-2022-01-22-18-08-51.png)
  - 链接是永久的，而且仅需要每个来源一个链接（复用性）
  - 流控制：组织发送方向接受方发送大量数据的机制
  - 服务器推送
## HTTPS
- 概述
  - HTTPS：Hypertext Transfer Protocol Secure
  - 经过TSL/SSL加密
  - 加密
    - 对称加密：加密和解密都是使用同一个密钥
    - 非对称加密，加密和解密需要使用两个不同的密钥：公钥（public key）和私钥（private key）
  - ![20220122182333-2022-01-22-18-23-34](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122182333-2022-01-22-18-23-34.png)
# 常见场景
控制台：network
- 静态资源（CSS）index.XXXX.css
  - Status Code
  - ![20220122184059-2022-01-22-18-40-59](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122184059-2022-01-22-18-40-59.png)
  - ![20220122184204-2022-01-22-18-42-05](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122184204-2022-01-22-18-42-05.png)
  - 静态资源方案：缓存+CDN+文件名hash
    - CDN：Content Delivery NetWork（链接分发网络）
    - 通过用户就近性和服务器负载的判断，CDN确保内容以一种极为高效的方式为用户的请求提供服务
- 业务场景-登录
  - ![20220122184855-2022-01-22-18-48-55](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122184855-2022-01-22-18-48-55.png)
  - ![20220122185104-2022-01-22-18-51-04](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122185104-2022-01-22-18-51-04.png)
    - 跨域：scheme（协议），Host name，port（端口号）有区别即为跨域
    - ![20220122185252-2022-01-22-18-52-53](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122185252-2022-01-22-18-52-53.png)
    
    *http默认80，https默认443.
    - 请求处理（大部分）

    ![20220122185520-2022-01-22-18-55-21](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122185520-2022-01-22-18-55-21.png)
    - 跨域解决方案：
      - CORS
      - 代理服务器：同源策略是浏览器的安全策略，不是HTTP的
       
        ![20220122185845-2022-01-22-18-58-46](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122185845-2022-01-22-18-58-46.png)

      - Iframe：有诸多不便
  - ![20220122190236-2022-01-22-19-02-37](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122190236-2022-01-22-19-02-37.png)

    1. 使用POST方法项目标域名http://sso.toutiao.com，目标path/quick_login/v2/
    2. 携带信息：Post body，数据格式为form；希望获取的数据格式为json；已有的cookie
    3. 返回信息：数据格式json；种cookie的信息
    - 鉴权：
    - Session+cookie携带登录信息
    - JWT（JSON web token）
    - ![20220122190845-2022-01-22-19-08-46](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122190845-2022-01-22-19-08-46.png) 
  - 跳转后网站自动登录
    - SSO（单点登录）解决方案
        ![20220122191333-2022-01-22-19-13-34](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122191333-2022-01-22-19-13-34.png)
# 实际应用
- 发起HTTP协议
  - 浏览器
  
    ![20220122191635-2022-01-22-19-16-35](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122191635-2022-01-22-19-16-35.png)

    ![20220122191915-2022-01-22-19-19-15](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122191915-2022-01-22-19-19-15.png)
  - node
  
    ![20220122192023-2022-01-22-19-20-24](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122192023-2022-01-22-19-20-24.png)
  - 请求库：axios
  
    ![20220122192052-2022-01-22-19-20-53](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122192052-2022-01-22-19-20-53.png)

  - 网络优化（稳定性）

    ![20220122192200-2022-01-22-19-22-01](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122192200-2022-01-22-19-22-01.png)

  - 稳定性

    ![20220122192333-2022-01-22-19-23-34](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122192333-2022-01-22-19-23-34.png)
# more
- WebSocket-通信方案
  - 浏览器与服务器进行全双工通讯的网络技术
  - 典型场景：实时性要求高，例如聊天
  - URL使用ws://或wss://等开开头
  - ![20220122192528-2022-01-22-19-25-29](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122192528-2022-01-22-19-25-29.png)
- QUIC（Quick UDP Internet Connection）
  - 目前不太常用
  - O-RTT建联（首次建联除外）。
  - 类似TCP的可靠传输。
  - 类似TLS的加密传输，支持完美前向安全。
  - 用户空间的拥塞控制，最新的BBR算法。
  - 支持h2的基于流的多路复用，但没有TCP的HOL问题。
  - 前向纠错FEC。
  - 类似MPTCP的Connection migration
  - ![20220122192725-2022-01-22-19-27-25](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122192725-2022-01-22-19-27-25.png)
  - ![20220122192736-2022-01-22-19-27-36](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220122192736-2022-01-22-19-27-36.png)