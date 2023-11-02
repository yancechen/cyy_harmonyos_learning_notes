HarmonyOS 初学者一枚，本文档记录上手 HarmonyOS 期间遇到的各种问题。

# 1、Dev-Eco Studio 无法识别本地模拟器

？？？？？？

问题描述：首次安装 Dev-Eco Studio，然后创建模拟器后，Dev-Eco Studio 能识别出模拟器，并成功运行。然而，第二天打开 Dev-Eco Studio工具，死活识别不了模拟器了🤪

# 2、File 'xxx/entry/src/main/ets/pages/ToDoList.ets' is not a module.

问题描述：自定义了一个组件，然后在其他页面引用（import）时提示该错误。

解决方案：为自定义组件加上关键字 `export default`。

```js
@Component
export default struct ToDoList {
  @State title: string = '待办'

  build() {
    Column() {
      Text(this.title)
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
    }
    .height('100%')
  }
}
```

原因：在一个模块内，内部声明的变量，函数，类等是无法在另外一个模块内访问到，如果需要访问，需要先通过 es6 提供的指令 export,export default 先导出， 然后再使用 import 导入使用。

参考：
- [《一篇文章带你看懂export、export default 命令差异》](https://juejin.cn/post/6844903971891445773)
- [《es6的export和export default指令》](https://juejin.cn/post/6996313710067187720)

# 3、There should have a root container component.

问题描述：自定义了一个组件，然后在其他页面使用时提示该错误。源码如下：

```js
//ToDoList是我自定义的组件

import ToDoList from './ToDoList'

@Entry
@Component
struct Index {
  @State message: string = 'Hello World'

  build() {
    ToDoList().height('100%')
  }
}
```

问题原因：自定义组件无法作为 root container。

解决方案：build() 里放一个布局组件，比如Row(), Column(), Flex()，然后再添加自定义的组件。

# 3、A page configured in 'main_pages.json' must have one and only one '@Entry' decorator.
