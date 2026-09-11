# GitHub Pages 项目网站交付

## 交付地址

计划最终入口：`https://windviolett.github.io/paper-reader/`（尚未部署）。

已确认 GitHub 连接账号是 `windviolett`，仓库 `windviolett/paper-reader` 已创建，默认分支为 `main`。使用普通项目仓库，不是 `windviolett.github.io` 个人主页仓库；不配置自定义域名或 CNAME。上线状态以实际 Pages 工作流结果为准。

## 仓库与 Pages 设置

仓库已由用户创建并初始化 README。当前 GitHub 连接提供文件写入接口，但不提供修改 Pages 设置的接口；初次开启 Pages 需在 GitHub 网页完成：

1. 打开 [Pages 设置](https://github.com/windviolett/paper-reader/settings/pages)。
2. 在 Build and deployment → Source 选择 GitHub Actions。
3. 在 [Actions](https://github.com/windviolett/paper-reader/actions) 查看发布工作流。若首次发布因未启用 Pages 失败，开启后重新运行对应工作流。

这里只需在 GitHub 网页登录，不需要在聊天中提供密码或 Token。

## 当前原型如何发布

1. 将 `paper-reading-site/` 内的内容作为专用 GitHub 仓库根目录，包含 `.github/` 隐藏目录；不要上传上一级工作区。
2. 本工作流默认使用 `main` 分支；如实际分支不同，修改工作流分支配置。
3. 在仓库 Settings → Pages → Build and deployment 中选择 GitHub Actions。
4. 推送文件到 `main`，或在 Actions 页面手动运行 `Publish reading prototype to GitHub Pages`。
5. 工作流成功后，以部署步骤给出的实际 URL 为准，打开并检查页面和资源。

GitHub Free 的默认方案是公共仓库；如需私有源码，发布前核对账号计划对 Pages 的支持。不要将后端凭据、用户论文或处理记录提交进仓库。

工作流只将明确列出的静态文件复制到 `_site/` 发布，不会把整个项目目录上传到 Pages。前端后续新增资源或替换为构建工具时，需要同步更新构建与文件清单。当前工作流发布的仍是明确标注为虚构演示的原型。

## 真实网站的部署分工

```text
https://<用户名>.github.io/<仓库名>/
    └── 静态前端：上传界面、任务状态、报告阅读、PDF 预览
          └── HTTPS 请求 → 独立后端 API
                             ├── 认证、任务和报告
                             ├── Worker → LLM API
                             └── 私有文件存储、数据库
```

- 后端可使用其托管平台默认 HTTPS 网址，不要求购买域名。
- 前端公开配置保存 API 地址；LLM API Key 只保存在后端环境变量／密钥管理中。
- CORS 允许的 origin 是 `https://<用户名>.github.io`，不包含 `/<仓库名>/`；同一账号的不同项目共享 origin，因此必须另做认证和任务归属校验。
- Pages 静态资源使用相对路径或构建时设置仓库 base path；首版页面路由使用 hash，确保刷新后可恢复。
- 上传、后台处理、长期存储和多用户历史由后端负责，不能依赖 Pages 或 GitHub Actions 充当运行中的论文处理服务。
- PDF 下载、预览和导出遵循用户权限；报告不得公开存入站点目录。

## 最终线上验收

从实际项目网址出发，在电脑和手机浏览器验证：上传真实论文 → 任务完成 → 报告与来源核对 → 修改保存 → 导出 → 刷新后恢复历史。另验收任务失败、未登录或无权限访问、后端不可达的提示。实际论文事实准确性沿用 `product-spec.md`。

确认 CSS、脚本、文档链接和 PDF 预览在仓库子路径下均可用；仅本地根路径下通过不算上线通过。记录前后端实际地址、部署版本和真实样本结果。提交源码、配置示例、部署步骤和运行费用说明。

当前交付的是静态阅读原型及发布配置。成功上传文件不代表 Pages 已部署成功；真实论文处理后端仍待开发。

## 官方参考

- [GitHub Pages 介绍与项目网址](https://docs.github.com/en/pages/getting-started-with-github-pages/what-is-github-pages)
- [使用 GitHub Actions 发布 Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages)
