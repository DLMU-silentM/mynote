# 攻击
## XSS
- 盲目信任了用户提交的字符串并直接复制给了DOM。
- 通常难以从UI上感知（暗地执行脚本）
- 取户信息（cookie/token）
- 绘制UI（例如弹窗），诱骗用户点击/填写表单
- 分类
  1. Stored XSS
       - 恶意脚本被存在数据库中
      - 访问页面->读数据 = 被攻击
      - 危害最大，对全部用户可见
  2. Reflected XSS
      - 不涉及数据库
      - 从URL上攻击
  3. DOM-based XSS
      - 需要服务器的参与
      - 恶意攻击的发起+执行，全在浏览器完成
  4. Mutation-based XSS
      - 利用了浏览器渲染DOM的特性（独特优化）
      - 不同浏览器，会有区别（按浏览器进行攻击）
## CSRF（跨站伪造请求）
- 在用户不知情的前提下
- 利用用户权限（cookie）
- 构造指定HTT请求，窃取或修改用户敏感信息
- iframe攻击
  
  ![20220125220725-2022-01-25-22-07-26](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220125220725-2022-01-25-22-07-26.png)
## Injection（注入）
- ![20220125205911-2022-01-25-20-59-13](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220125205911-2022-01-25-20-59-13.png)
- CLI（命令行）
- OS commend
- Sever-Side Request Forgery（SSRF），服务端伪造请求。（严格来说，SSRF不是Injection，但是原理类似）
## DoS
通过某种方式（构造特定请求），导致服务器资源被显著消耗，来不及响应更多请求，导致请求挤压，进而雪崩效应。
1. ReDoS：基于正则表达式的DoS
2. DDos
   短时间内，来自大量僵尸设备的请求流量，服务器不能及时完成全部请求，导致请求堆积，进而雪崩效应，无法响应新请求。
   - 攻击特点
     - 直接访问IP
     - 任意API
     - 消耗大量带宽（耗尽）
3. 中间人攻击
   - 明文传输
   - 信息篡改不可知
   - 对方身份未验证
# 防御
## 防御XSS
永远不信任用户的提交内容，不要将用户提交内容直接转换成DOM
### 工具
- 前端
  - 主流框架默认防御XSS
  - google-closure-library
- 服务端
  - DOMPurify
### 同源策略Same-origion Policy
- 协议
- 域名
- 端口
## CSP（链接安全策略）
- 那些源（域名）被认为是安全的
- 来自安全源的脚本可以执行，否则直接抛错
- 对 eval + inline scripti拒绝
## CSRF防御
- origion+referrer

    ![20220125220411-2022-01-25-22-04-12](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220125220411-2022-01-25-22-04-12.png)
- token
  
  ![20220125220536-2022-01-25-22-05-36](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220125220536-2022-01-25-22-05-36.png)
- CSRF anti-pattern
- 避免用户数据被携带：SameSite Cookie
  
  ![20220125221251-2022-01-25-22-12-52](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220125221251-2022-01-25-22-12-52.png)
  
  ![20220125221351-2022-01-25-22-13-52](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220125221351-2022-01-25-22-13-52.png)
  - 限制的是cookie domain，页面域名
  - 依赖于Cookie的第三方服务：`Set-Cookie: Samesite=None; Secure;`
## Injection防御
- 找到项目中查询SQL的地方
- 使用prepared statement