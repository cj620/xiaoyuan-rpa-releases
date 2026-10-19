# xiaoyuan-rpa Releases

本仓库只用于公开分发 xiaoyuan-rpa 桌面端安装包。

请从 [Releases](https://github.com/cj620/xiaoyuan-rpa-releases/releases) 下载对应平台的安装包和校验文件。

当前支持 macOS Apple Silicon（DMG）和 Ubuntu 24.04 x86_64（DEB），以同一版本、同一源码提交的 Pre-release 一同发布。
macOS 安装包尚未进行 Apple Developer ID 签名或公证，仅用于内部验收。

Ubuntu 下载 DEB 后运行 `sudo apt install ./xiaoyuan-rpa-desktop-setup-<version>-linux-x64.deb`，随后从应用菜单启动，或运行 `ai-rpa --help`。使用已登录的桌面会话并解锁登录密钥环；普通浏览器需另装 Chrome/Chromium，紫鸟任务需安装 Linux 紫鸟并配置账号。

GitHub Actions 的 `发布 macOS 与 Ubuntu 桌面端预发布版` 接受共同版本号及私有源码的完整 SHA。默认只构建和验证；选择 `publish` 后，两端都成功才发布同一个 Release。沿用 `desktop-mac-v<version>` 标签以兼容旧版 Mac 更新检查。
