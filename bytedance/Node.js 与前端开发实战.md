# Node.js应用场景
## 前端工程化
- Bundle：webpack，vite，esbuild，parcel
- Uglify：uglifyis
- Transpile：bablejs，typescript
- 其他语言加入竞争：esbuild，parcel，prisma
- 现状：难以替代
## Web服务端应用
- 学习曲线平缓，开发效率较高
- 运行效率接近常见的编译语言
- 社区生态丰富及工具链成熟（npm，V8 inspector）
- 与前端结合的场景会有优势（SSR）
- 现状：竞争激烈，Node.js有自己独特的优势
## Electron跨端桌面应用
- 商业应用：vscode，slack，discord，zoom
- 大型公司内的效率工具
- 现状：大部分场景在选型时，都值得考虑
# Node.js运行时结构
## 结构
![20220124192449-2022-01-24-19-24-50](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220124192449-2022-01-24-19-24-50.png)
- V8：JavaScript Runtime，诊断调试工具（inspector）
- libuv：eventloop（事件循环），syscall（系统调用）
- 举例：用node-fetch发起请求时...
## 特点
- 异步IO
  - Node.js执行IO操作时，会在响应返回后恢复操作，而不是阻塞线程并占用额外内存等待。
  - ![20220124193536-2022-01-24-19-35-37](http://lengyuewusheng-blog.oss-cn-beijing.aliyuncs.com/blog/20220124193536-2022-01-24-19-35-37.png)
- 单线程（现在可以通过worker_thread模块起新线程）
  - 实际：JS线程+uv线程+V8线程池+V8 Inspector线程，实际上是主线程单线程。
  - 优点：不用考虑多线程状态同步问题，也就不需要锁；同时还能比较高效地利用系统资源；
  - 缺点：阻塞会产生更多负面影响
  - 解决办法：多进程或多线程
- 跨平台
  - 大部分功能，API。但也有一些单系统特有API。
  - Node.js跨平台+ JS无需编译环境（+ Web跨平台+诊断工具跨平台）= 开发成本低（大部分场景无需担心跨平台问题），整体学习成本低
# 编写HTTP Server
## 安装
- Mac，Linux推荐使用nvm。多版本管理。
- Windows推荐nvm4w或是官方安装包。
- 安装慢，安装失败的情况，设置安装源。NVM NODEJS ORG MIRROR=https://npmmirror.com/mirrors/node nvm install 16
# 延伸