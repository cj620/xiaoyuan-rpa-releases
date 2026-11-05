# xiaoyuan-rpa Releases

本仓库只用于公开分发 xiaoyuan-rpa 桌面端安装包。

请从 [Releases](https://github.com/cj620/xiaoyuan-rpa-releases/releases) 下载对应平台的安装包和校验文件。

当前支持 Windows x64（EXE）和 macOS Apple Silicon（DMG），以同一版本、同一私有源码提交共同构建；两端回归、静态检查和包内冒烟全部成功才发布。
macOS 安装包尚未进行 Apple Developer ID 签名或公证，仅用于内部验收。

Ubuntu 已于 2026-11-05 停止构建与维护，仅保留历史安装包。历史 DEB 下载后运行 `sudo apt install ./xiaoyuan-rpa-desktop-setup-<version>-linux-x64.deb`，随后从应用菜单启动，或运行 `ai-rpa --help`。使用已登录的桌面会话并解锁登录密钥环；普通浏览器需另装 Chrome/Chromium，紫鸟任务需安装 Linux 紫鸟并配置账号。

GitHub Actions 的 `发布 Windows 与 macOS 桌面端` 接受共同版本号及私有源码的完整 SHA。默认只构建和验证；选择 `publish` 后，两端都成功才准备同一个 Release 草稿，并上传、回读校验附件。Gitea 统一交付流程跟踪固定的 GitHub run，验证两端 artifacts 和内网草稿后依次公开两边 Release，最后验收官网下载。直接运行 GitHub 工作流不会自动公开草稿。沿用 `desktop-mac-v<version>` 标签以兼容旧版 Mac/Ubuntu 更新检查；工作流文件名 `publish-macos.yml` 保留为原入口。

稳定版包含原 Ed25519 更新密钥签署的 `latest.json`，供新版 Windows 自动校验和安装。预发布不包含稳定清单，也不替换 Latest。Windows 默认使用现有内网无 Authenticode 证书方式，配置证书后可选 `production`；macOS 仍未签名、公证。首次迁移的 Windows 过渡包继续保留；后续发行同步到 GitHub 与 Gitea，官网下载实时读取已公开的内网版本。

公开仓库仅保存分发配置、安装包和摘要，不包含私有源码或密钥。维护者在 Actions Secrets 中保留只读 `AI_RPA_SOURCE_DEPLOY_KEY` 和原 `DESKTOP_UPDATE_SIGNING_KEY`，无需 Gitea 或内网构建凭据。
