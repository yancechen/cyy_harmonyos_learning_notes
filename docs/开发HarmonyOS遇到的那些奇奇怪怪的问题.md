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

问题描述：自定义了一个组件，然后在标记了 @Entry 的 Index 页面里进行了引用，报了该错误。

原因分析：我创建自定义组件的方式是：new -> Page

<img width="520" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/491afcb0-016a-478e-8846-2b5f9d97c8d3">

创建好以后，会在 `main_pages.json` 里生成自己创建的页面路径：

<img width="401" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/c2a1b62c-aa60-4ff6-8ec6-a2a4d98ad47c">

而 `main_pages.json` 的作用是**配置所有需要进行路由跳转的 page 页面的路由信息**，而我们只是需要一个可以复用的 UI 组件，不是页面，因此，此种创建方式不正确。

解决方案 1：手动删除 `main_pages.json` 的配置

<img width="319" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/b386746c-c7c2-4594-927b-5c4d08124e88">

解决方案 2：创建自定义的组件的方式改为：new -> ArkTS File

<img width="453" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/ff24591d-05df-4938-9429-1f480a16a6c0">


