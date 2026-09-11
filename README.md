# AI 论文结构化阅读网站 · 产品原型

本阶段交付：阅读报告样稿、可交互的静态网页、首版产品与验收规范。

**已确定的最终交付形式：GitHub Pages 项目网站 `https://<用户名>.github.io/<仓库名>/`，无需自购域名。** 前端在 Pages 发布，真实 PDF 处理与 LLM 调用由另行部署的后端提供。当前原型还未上线，不能作为完整功能交付。

GitHub 仓库：[windviolett/paper-reader](https://github.com/windviolett/paper-reader)。计划网站入口：[windviolett.github.io/paper-reader](https://windviolett.github.io/paper-reader/)。仓库已经创建；网站是否上线以 GitHub Actions 的 Pages 部署结果为准。

- 打开 `index.html` 查看原型，无需安装依赖。
- `docs/sample-report.md` 是可阅读、可修改的报告样稿。
- `docs/product-spec.md` 定义后续真实产品的范围、数据约定与验收方法。
- `docs/deployment.md` 说明项目网址、发布方式和最终线上验收要求。
- `.github/workflows/pages.yml` 是准备好的静态原型发布工作流，默认分支为 `main`。

原型可以切换速览与精读、展开方法和术语说明、查看示例证据卡、下载 Markdown 和通过浏览器打印／保存 PDF。

**所有论文名称、方法、数据与引用均为虚构演示。未接入 LLM、未处理真实 PDF，不包含真实原文预览。** 页码按钮打开的是示例证据卡，不是已经验证的原文定位。

下一开发里程碑：选择真实 AI 方法论文，配置服务端模型接入，跑通 PDF → 带来源的事实记录 → 报告 → 原文定位的最小闭环。
