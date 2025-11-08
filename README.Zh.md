# Rabbit-TEA
- >作者：Yoorkin
- >项目描述：MoonBit的TEA Web UI框架
- >[API文档](https://mooncakes.io/docs/Yoorkin/rabbit-tea)
---
- >读者：evinyang
- >时间：2025年11月7日
---
- 一个受`Elm 架构`启发的声明式和函数式 Web UI 框架。
---
# 特点
## 重构安全
- 利用模式匹配和标记联合，检查机制提供了更好的重构体验
- 防止运行时错误，确保健壮和可靠代码
## 可维护状态
- 全球管理状态使APP维护更容易
- 利用`moonbitlang/core/immut`中的持久化数据结构可轻松实现撤销/重做等高级功能
## 轻量级运行时
- 比如一个项目经压缩生成js文件大小为33kb包括虚拟DOM
---
# 基础示例
```mbt
typealias Int as Model
let model = 0

enum Msg {
  Increment
  Decrement
}

fn update(msg : Msg, model : Model) -> (Cmd[Msg], Model) {
  match msg {
    Increment => (none(), model + 1)
    Decrement => (none(), model - 1)
  }
}

fn view(model : Model) -> Html[Msg] {
  div([
    h1([text(model.to_string())]),
    button(click=Increment, [text("+")]),
    button(click=Decrement, [text("-")]),
  ])
}

fn main {
  @tea.startup(model~, update~, view~)
}
```
---
# 开始使用
- 使用该框架的模板项目：[Rabbit-TEA template](https://github.com/evinyang-zw/rabbit-tea-template.git)
- 项目包含使用`Rabbit-TEA`调试代码的说明