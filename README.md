方块战舰工具 · 发布仓库
========================

本仓库**只承载 GitHub Releases**：产物作为 Release 资产挂在 tag 上，
源码在另一个互相独立的仓库 `FKEditor`。工作树**不提交任何二进制**。

每个版本对应一个 tag（如 `v2.1.0`）与一个 Release，资产统一命名为
`FKEditor-<平台>-v<版本>[后缀].<扩展名>`：

    FKEditor-Desktop-v<版本>.exe          便携版主程序
    FKEditor-Desktop-v<版本>-setup.exe    NSIS 安装器
    FKEditor-Desktop-v<版本>.msi          MSI 安装器
    FKEditor-Android-v<版本>.apk          直装包（arm64-v8a）
    FKEditor-Android-v<版本>.aab          上架包（Google Play）
    latest.json                           自描述清单（机器可读，更新器读它）

同一版本的桌面端与移动端**锁步**发在同一个 Release 里，`latest.json`
的 `platforms` 同时含 `windows-x64`（installer / portable）与
`android-arm64`（install / bundle）两组键，两侧读同一份清单。

构建脚本（`FKEditor/tools/release-manager/build-*.ps1`）会把产物直接落到
**本仓库根目录**，与 `gh release create` 上传的资产同名同源；工作树不提交
二进制（见 .gitignore）。

应用更新读取 GitHub API 的最新 Release（公开仓库免认证）：

    GET https://api.github.com/repos/LLL-lyh0/FK-Releases/releases/latest

发布由源码仓库中的 `tools/release-manager`（发布管理器）通过 `gh release create`
完成 —— 本机 `gh` 已登录即无需任何令牌。

`.stage/` 是发布管理器准备资产用的本地暂存目录，已被 .gitignore 忽略。
