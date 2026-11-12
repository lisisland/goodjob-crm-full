# GoodJob CRM 完整版（华橙本地定制）

保留 GoodJob 原有完整工作区，包含客户管理、获客、商机、触达、通信及其他业务模块。本仓库同时保留本地新增的精简入口与电商资料模块，便于对照和继续二开。

- 完整版：启动前端后访问 `/`。
- 精简入口：访问 `/focus.html`。
- 独立精简源码仓库：[huacheng-leads-lite](https://github.com/lisisland/huacheng-leads-lite)。

## 启动与数据

此上传为源码备份，不含本机运行环境、MySQL、账号密码或真实客户数据库。现有电脑上的项目继续位于 `<LOCAL_PROJECT_DIR>`，上传操作不迁移或覆盖它。

环境要求：Node.js 24、npm、MySQL 8；完整通信服务可选配置见上游说明。

```bash
npm ci
npm --prefix whatsapp-plugin install --workspaces=false
```

首次部署先按 [上游部署说明](README.upstream.md) 配置独立数据库及本地环境文件；`.env.example` 仅为占位示例，必须更换所有密钥和数据库密码。仓库没有附赠可登录的真实管理员账号。

使用上游标准流程：`npm run db:profiles:provision` 配置数据库档位，按 `npm run db:profiles:status` 检查，再使用 `npm run dev` 启动。有关初始化、账号与部署的细节以随仓库保存的上游文档和部署脚本为准；此上传没有验收空白机器全新安装。

原电脑的本地启动脚本 `start-desktop.ps1` / `start-local.ps1` 是已有环境的便利入口，涉及本机 MySQL 路径及 14188/15188/13100/15193 端口，不是通用安装器。在新电脑运行前须自行配置环境。

获客、背调、模型和搜索服务的调用取决于自行配置的凭据。自动发信与电商采集并非所有渠道均已通过实网验收。非洲电商有三平台定义、解析与导入，既往在线测试存在 403 和连接失败；没有把失败包装成采集成功。

## 上游与许可证

基于 [huangguojia/GoodJob](https://github.com/huangguojia/GoodJob)，本次为本地安装版本的独立源码快照，不声称与上游最新提交完全一致。核心保留 Apache-2.0；独立通信服务按其 GPL-3.0 与第三方 NOTICE 处理。详见 [LICENSE](LICENSE)、[NOTICE](NOTICE)、[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) 和 `LICENSES/`。本地修改日期及边界见本文档与 `docs/`。

2026-11-12 变更：整理双版本仓库、补充说明、排除本机凭据与业务数据。沿用 2026-10 的精简 UI 和电商公开资料模块。未包含真实客户、邮箱授权码、API Key、WhatsApp 登录会话或运行截图。

## 公开展示版本的数据边界

此仓库已去除本机凭据、个人目录、客户数据库与运行资料。开发种子及测试中的部分联系资料改为保留域名 `.example`；它们仅为演示，不能用于真实联系。

上游 Excel 样例含预填商业信息及嵌入图片，故未随公开仓库发布。单据导出需自行配置脱敏模板，见 `backend/resources/document-templates/README.md`。源码功能保留，不提供样例银行信息或签章。前端构建已验证；未验收空白机器首次安装或实际外部服务投递。

原始上游说明保存在 `README.upstream.md`，其中描述的模板或本地环境不一定包含于本公开快照。上游版权和许可证归属保持不变。
