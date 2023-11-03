近期完整的体验了一下 HarmonyOS 应用开发，特此记录下开发过程中的一些感受。

# 好的体验

## 1. 详细、可用的文档

HarmonyOS 配套的开发文档非常丰富，并且结构目录很清晰，不像其他技术栈的官方文档，在文章之间来回跳来跳去几次后，就不知道自己在那个位置了。

另外，由于本身就是中文文档，因此语言上更容易理解，不像很多英文文档在翻译为中文后，由于翻译水平太差，导致读不懂的尴尬。

<img width="1409" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/cba416c1-0610-4307-85cb-fa6d4d6fbdec">

## 2. 上手成本低

ArkTS 在 TypeScript 的基础上，扩展了声明式 UI，因此对于前端开发同学来说，上手 ArkTS 的成本非常低，对于客户端同学来说，如果写过 Flutter，那么上手 ArkTS 也是很容易的。

## 3. 更加容易的状态管理

ArkTS 也是在 TypeScript 的基础上，扩展了状态管理，提供了各种装饰器（其实就是注解）来实现组件内部、父子组件的状态同步和自动刷新。

如果你体验过 Flutter 状态管理的方式，那么 ArkTS 的状态管理会让你感觉很爽。

状态管理参考文档：https://developer.harmonyos.com/cn/docs/documentation/doc-guides-V3/arkts-state-management-overview-0000001524537145-V3?catalogVersion=V3

# 不好的体验

## 1. Dev-Eco Studio 不识别本地模拟器

这个问题其实很早就有人提出来，但是一直没有得到一个有效的解决方案，更不清楚具体的原因。

我单独发了一个帖子，想看看官方的回复。

<img width="928" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/ec7e3263-4953-4ed4-bb0b-df02683c6b16">

## 2. Dev-Eco Studio 体验有待提升

如果你用过高版本的 Android Studio 或者 IntelliJ IDEA，再回来使用 Dev-Eco Studio，有一种从现代化回归原始的感觉。当然，这个不是什么大问题，相信后面 HarmonyOS 团队会持续优化开发工具。

Dev-Eco Studio：

<img width="1490" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/ea56c4c4-8a65-4825-8c16-41360c7ee321">

Android Studio：

<img width="1519" alt="image" src="https://github.com/yancechen/cyy_harmonyos_learning_notes/assets/19757728/682515d2-8d09-48b2-b859-fd7f743a0aa3">

## 3. 开发者文档频繁提示需要登录

这个体验真的很不好。

首先，浏览开发者文档的内容需要进行登录，然后文档平台的登录态只能保存几个小时。如果你看了文档，然后又去处理其他事情，等你再回来就会让你登录。

而且不会保存你的登录账户，每次都需要重新输入，有点崩溃🤪。
