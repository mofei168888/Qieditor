<p align="center">
 <img width="100px" src="./docs/images/logo.svg" align="center" alt="Tnshare Logo" />
 <h2 align="center">Qieditor</h2>
 <p align="center">Qieditor 是一个 HTML 页面生成器：通过配置形式快速生成页面的可视化编辑工具，做到一次开发、多次生成，简化开发流程，提高开发流水线的生产效率。</p>
</p>
<p align="center">
  <a href="https://github.com/Qionline/Qieditor/issues/new/choose">提供新点子 💡</a>
  |
  <a href="https://github.com/Qionline/Qieditor/issues/new/choose">报告BUG 🐛</a>
  |
  <a href="https://github.com/Qionline/Qieditor/pulls">提交PR 🔀</a>
</p>

<p align="center">
  点击 <a href="https://qi.byeguo.cn/">🥳 立即使用 🥳</a> 即可体验 Qieditor 的完整功能。
</p>

## 功能介绍

目前 Qieditor 支持如下功能：

**基础功能：**

- [x] 配置文件导入导出
- [x] 生成可用的HTML页面
- [x] 组件客制化编辑
- [x] 拖拽组件自定义顺序

**增强功能：**

- [x] ios / android 机型模拟：用于解决根据ios/android机型触发不同页面逻辑的需求。
- [x] 本地自动存储：为解决编辑过程中浏览器闪退等导致编辑内容丢失的问题。

## 文件配置项

Qieditor 通过解析导入.json的配置文件来生成可视化编辑页面，配置文件规则如下：

```json
{
  "filename": "导出html时文件名称",
  "global": {
    "title": "tab栏中的名称，即document.title",
    "direction": "ltr",
    "bodyColor": "#e07300",
    "css": "body{color:#fff}",
    "js": ""
  },
  "main": [
    {
      "id": 1,
      "name": "侧边栏中显示的内容",
      "params": {
        "aParam": {
          "type": "text",
          "title": "右侧组件配置中显示的内容",
          "value": "可编辑的值：我是aParam"
        }
      },
      "htmlstr": "<div>我是main <%aParam%> </div>"
    }
  ],
  "component": [
    {
      "id": 2,
      "name": "与main相同",
      "params": {},
      "htmlstr": "<div>我是component</div>"
    }
  ]
}
```

你可以尝试创建json文件并将此导入Qieditor中，快速的熟悉配置的用法。

### 注意

这里主要说几项需要注意的配置：

- `global.direction`:
- `global.css`与`global.js`:
- main与component中: 组件项的结构是相同的，但是注意id不能重复，这是用于区分不同组件的标识。
- params中，key是用户自定义的，其值会在渲染htmkstr时通过<%key%>的形式使用。

## 解析流程

解析流程如图所示：

1. 首先开发者编写可用的配置文件
2. 将配置文件导入进Qieditor
3. Qieditor生成可导出的html
4. 与此同时，Qieditor会进行本地存储、注入展示页面可用的js脚本文件，进而生成可预览的html
5. 此时交予使用者进行页面配置、在配置完毕后生成可用的html文件。

![](./docs/images/mind.png)

## 最后

本项目完全开源，如果你有好的想法，或者在使用过程中遇到了什么问题，欢迎通过issure与我交流。

都看到这里了希望你可以点一个star🌟支持一下～


