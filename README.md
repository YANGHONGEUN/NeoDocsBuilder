# NeoDocsBuilder 

NeoDocsBuilder —— 一个超牛逼的 NEO 文档编译、生成工具

| 周期 | 功能                     | 状态     | 说明                                                         | 开源库                                 |
| ---- | ------------------------ | -------- | ------------------------------------------------------------ | -------------------------------------- |
| 1    | MarkDown 解析            | 已完成   | 对 MarkDown 文档进行解析                                     | Microsoft.Toolkit.Parsers.Markdown     |
| 1    | MarkDown - HTML 的转换   | 已完成   | 将已解析的 MarkDown 转换为 HTML                              |                                        |
| 1    | 多文档自动转换           | 已完成   | 针对一个文件夹内的多级目录以  及多个 .md 文件自动生成 HTML   |                                        |
| 1    | bootstrap4 集成          | 已完成   | 生成带 bootstrap4 样式的 HTML                                |                                        |
| 1    | 文档目录的自动生成       | 已完成   | 自动根据目录结构生成文档目录  以代替之前手动修改 .yml 文档的工作 |                                        |
| 1    | 目录中文件夹的自定义配置 | 已完成   | 配置 folder.json 实现文件夹的重命名和隐藏                    |                                        |
| 1    | 网站模板                 | 基本完成 | 开发 docs.neo.org 的前端页面的模板                           |                                        |
| 1    | 自适应 HTML 编码         | 基本完成 | 根据 MarkDown 中的标签内容，进行正确的 HtmlEncode，  以使某些标签按文本显示，某些标签按代码显示 |                                        |
| 1    | 动态目录生成             | 已完成   | 为每篇文档生成不同的相对路径的目录，  以兼容 [file://](file:///) 协议 |                                        |
| 1    | 文章摘要和锚点的自动生成 | 已完成   | 为每篇文档自动生成右侧的章节列表，  点击可进行文档内的跳转   |                                        |
| 1    | 滚动监听                 | 已完成   | 右侧章节列表的滚动监听，文章滚动到某个章节，右侧章节列表高亮显示 | bootstrap - scrollspy                  |
| 1    | 当前位置定位，及目录高亮 | 已完成   | 对当前阅读的文档和标题进行定位，在左侧目录和右侧摘要处高亮显示 |                                        |
| 1    | 懒加载                   | 已完成   | 对图片进行懒加载                                             | jquey.lazyload                         |
| 1    | 代码高亮                 | 已完成   | 对代码进行高亮显示                                           | highlight.js  Visual Studio-like style |
| 1    | 针对标题进行折叠展开     | 已完成   | 适用于 FAQ 之类的大量需要折叠的内容                          |                                        |
| 1    | 多语言切换               | 未完成   | 网站多语言切换以及内容的多语言切换                           |                                        |
| 1    | 标题搜索                 | 未完成   | 对文档标题进行搜索（前端）                                   |                                        |
| 2    | 全局搜索                 | 未完成   | 对网站内容进行全局搜索（后端）                               |                                        |
| 2    | 代码片段复制             | 已完成   | 一键复制文档中的代码片断                                     | clipboard.js                           |
| 2    | 版本切换                 | 未完成   | 在网站中可以设置版本，并且支持切换                           |                                        |
| 2    | 本地浏览                 | 已完成   | 兼容 [file://](file:///) 协议                                |                                        |
| 2    | 多主题切换               | 未完成   | 支持自定义主题，GitHub 样式、夜间主题                        |                                        |
| 3    | 反馈建议                 | 未完成   | 支持文档的打分和反馈（以及时知道对开发者是否有帮助）         |                                        |

 

## 配置文件说明

**config.json** 

lazyload：是否开启懒加载

origin：存储 MarkDown 文件的文件夹，作为编译的输入

template：存储网站模板的文件夹，作为编译时候的模板

destination：存储编译结果的文件夹，作为编译的输出

```json
{
  "ApplicationConfiguration": {
    "lazyload": "true",
    "origin": "origin",
    "template": "template",
    "destination": "wwwroot"
  }
}
```

**folder.json**

rename：表示文件夹名和生成的目录结构中的的对应关系。

hidden：生成目录结构时需要隐藏的文件夹，一般是保存图片资源的文件夹。

collapse：生成文档内容时，对二级标题下的所有内容进行折叠，单击二级标题时展开内容，适用于大量需要折叠的内容，如 FAQ。

默认的目录顺序按照文件名和文件夹名排序，如果修改顺序可以通过修改文件夹名来实现，如 `1_folder`，或 `a_folder`。

```json
{
  "rename": {
    "basic": "基础知识",
    "node": "节点",
    "consensus": "共识机制",
    "exchange": "交易所对接指南"
  },
  "hidden": [
    "assets"
  ],
  "collapse":[
    "faq.md"
  ]
}
```

