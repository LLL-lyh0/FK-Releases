方块战舰工具 · 发布仓库
========================

本仓库**只承载 GitHub Releases**：产物作为 Release 资产挂在 tag 上，
源码在另一个互相独立的仓库 `FKEditor`。工作树**不提交任何二进制**。

每个版本对应一个 tag（如 `v2.1.0`）与一个 Release，资产约定：

    FKEditor.exe                    便携版主程序
    FKEditor_<版本>_x64-setup.exe   NSIS 安装器
    FKEditor_<版本>_x64_en-US.msi   MSI 安装器
    latest.json                     自描述清单（人工下载用）

应用更新读取 GitHub API 的最新 Release（公开仓库免认证）：

    GET https://api.github.com/repos/LLL-lyh0/FK-Releases/releases/latest

发布由源码仓库中的 `tools/release-manager`（发布管理器）通过 `gh release create`
完成 —— 本机 `gh` 已登录即无需任何令牌。

`.stage/` 是发布管理器准备资产用的本地暂存目录，已被 .gitignore 忽略。
