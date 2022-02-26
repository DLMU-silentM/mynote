# React历史与应用

## 使用场景

1. 前端应用开发

2. 移动端原生应用

3. 结合Electron，进行桌面应用开发

## 历史

1. 2010年Facbook 在其php生态中，引入了xhp枢架，首次引入了组合式组件的思想，启发了后来的React的设计

2. 2011年Jordan Walke创造了Faxts，也就是后来的React原型

3. 2012年在Facebook收购Instagram后，该FaxJS项目在内部得到使用，Jordan Walke基于FaxJS的经验创造了React

4. 2013年React正式开源，在2013 JSConf上Jordan Walke介绍了这款全新的彬架：

# React设计思路

- UI编程痛点
  
  - 状态更新，UI不会自动更新，需要手动地调用DOM进行更新。
  
  - 欠缺基本的代码层面的封装和隔离，代码层面没有组件化。
  
  - UI之间的数据依赖关系，需要手动维护，如果依赖链路长，则会遇到
    "Callback Hell"

系统

- 转换式系统：给定输入，求解输出（编译器，数值计算）

- 响应式系统：监听事件，消息驱动（监控系统，UI系统）
  
  事件->执行既定的回调->状态变更->UI更新

响应式编程

- 状态更新，UI自动更新。

- 前端代码组件化，可复用，可封装。

- 状态之间的互相依赖关系，只需声明即可。

总结

- 组件是组件的组合/原子组件

- 组件内拥有状态，外部不可见

- 父组件可将状态传入组件内部

组件化

- 组件声明了状态和UI的映射。

- 组件有Props/State两种状态。

- "组件"可由其他组件拼装而成。

# React（hooks）写法

![](C:\Users\74981\Pictures\Screenshots\屏幕截图(20).png)

![](C:\Users\74981\Pictures\Screenshots\屏幕截图(21).png)

# React实现

1. JSX不符合JS语法

2. 返回JSX发生改变时，如何更新DOM

3. State、Props更新时，要重新触发render函数

## Virtual DOM（虚拟DOM）

        Virtual DOM是一种用于和真实DOM同步，而在Js内存中维护的一个对象，它具有和DOM类似的树状结构，并和DOM可以建立一一对应的关系。
        它赋予了React声明式的API：您告诉React希望让UI是什么状态，React就确保DOM匹配该状态。这使您可以从属性操作、事件处理和手动DOM更新这些在构建应用程序时必要的操作中解放出来。

![](C:\Users\74981\Pictures\Screenshots\屏幕截图(22).png)

# React状态管理库

将状态抽离到UI外部进行统一管理

坏处：减低了组件复用性，一般用于业务代码中。

## 软件

redux，xstate，mobx，recoil

## 状态机

当前状态，收到外部事件，迁移到下一个状态

# 基于React应用级框架

1. NEXT.js

2. MODERN.js

3. Blitz
