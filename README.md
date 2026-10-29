# xiaoyuan-rpa Releases

本仓库只用于公开分发 xiaoyuan-rpa 桌面端安装包。

请从 [Releases](https://github.com/cj620/xiaoyuan-rpa-releases/releases) 下载对应平台的安装包和校验文件。

当前支持 Windows x64（EXE）、macOS Apple Silicon（DMG）和 Ubuntu 24.04 x86_64（DEB），以同一版本、同一私有源码提交共同构建；三端回归、静态检查和包内冒烟全部成功才发布。
macOS 安装包尚未进行 Apple Developer ID 签名或公证，仅用于内部验收。

Ubuntu 下载 DEB 后运行 `sudo apt install ./xiaoyuan-rpa-desktop-setup-<version>-linux-x64.deb`，随后从应用菜单启动，或运行 `ai-rpa --help`。使用已登录的桌面会话并解锁登录密钥环；普通浏览器需另装 Chrome/Chromium，紫鸟任务需安装 Linux 紫鸟并配置账号。

GitHub Actions 的 `发布 Windows、macOS 与 Ubuntu 桌面端` 接受共同版本号及私有源码的完整 SHA。默认只构建和验证；选择 `publish` 后，三端都成功才发布同一个 Release。沿用 `desktop-mac-v<version>` 标签以兼容旧版 Mac/Ubuntu 更新检查；工作流文件名 `publish-macos.yml` 保留为原入口。

稳定版包含原 Ed25519 更新密钥签署的 `latest.json`，供新版 Windows 自动校验和安装。预发布不包含稳定清单，也不替换 Latest。Windows 默认使用现有内网无 Authenticode 证书方式，配置证书后可选 `production`；macOS 仍未签名、公证。首次迁移的同一个 Windows 过渡包会在旧更新地址保留一次，之后安装包和更新仅发布到 GitHub。

公开仓库仅保存分发配置、安装包和摘要，不包含私有源码或密钥。维护者在 Actions Secrets 中保留只读 `AI_RPA_SOURCE_DEPLOY_KEY` 和原 `DESKTOP_UPDATE_SIGNING_KEY`，无需 Gitea 或内网构建凭据。
