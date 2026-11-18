# Codex 任务清单与侧栏 1.3.2

安装包包含会话任务卡和独立侧栏。侧栏显示同一份清单，关闭侧栏后，完整任务卡留在会话区。会话卡会自动读取已保存的进度。此版移除了会话卡上的「刷新进度」按钮。

## 安装

[下载 1.3.2 通用安装包](Codex-Checklist-1.3.2-macOS-Windows.zip)。解压前可在 GitHub 打开 ZIP 文件并选择 Download raw file。

1. 确认已安装 Codex 桌面客户端、Node.js 22 或以上（含 npm）和 Python 3.11 或以上。安装期间需要能访问 npm registry。Windows 使用原生 PowerShell，Node.js 使用自带 npm 的 Windows 安装版。
2. 安装或升级前退出 Codex。解压，打开终端并进入解压后的 `Codex-Checklist-1.3.2` 文件夹，运行：

   - macOS：`python3 install.py`
   - Windows：`py -3 install.py`（也可用 `python install.py`）

3. 完全退出并重新打开 Codex。需要试用时，在新会话说「用任务清单跟踪这个多步任务」。从卡片点「在侧栏显示」，Codex 会收到一条打开同一清单的请求。也可以从会话工具栏打开「清单面板 · 双卡片」。

安装器会在当前 Codex 配置目录注册两个本机 MCP 服务，沿用已有清单数据目录。默认配置目录为 `~/.codex`，已设置 `CODEX_HOME` 时使用该目录。Windows 的默认数据目录为 `%LOCALAPPDATA%\CodexTaskChecklist`。使用自定义目录时，放在支持文件硬链接的本地 NTFS 卷上。macOS 的默认数据目录为 `~/Library/Application Support/CodexTaskChecklist`。每位同事使用自己的本机数据。

## 让复杂任务默认建立清单

将 [AGENTS.snippet.md](AGENTS.snippet.md) 的内容附加到项目的 `AGENTS.md`，或附加到 Codex 配置目录下的全局 `AGENTS.md`。项目规则只影响本项目。已有清单规则时合并即可。偶尔使用时也可直接在会话里要求建卡。

## 从已有版本升级或回退

升级也运行同一安装命令。它会保留原数据目录和侧栏绑定，并保存升级前的 MCP 配置。安装时遇到无法识别的同名入口会停止，请先确认哪个服务占用了同名配置。

要回退，在原解压目录运行 `python3 install.py rollback`（macOS）或 `py -3 install.py rollback`（Windows），再重启 Codex。回退恢复升级前的配置，保留清单数据。安装后若另行修改过配置，回退命令会停下并给出备份路径，供手动合并。

## Windows 桌面快速检查

重开 Codex 后，在新会话要求用清单跟踪一个多步任务。检查会话卡是否出现、步骤是否自动更新，再打开并关闭右侧栏，确认会话卡仍能读到完整步骤。

## 验证范围

同一 ZIP 已在 Windows Server 2025（x64）和 macOS 通过回归。验证覆盖安装、旧配置升级、回退、MCP 读写、自动同步和中文路径。Windows Codex 桌面原生显示待实测。 [Windows 实跑记录](https://github.com/FF1911/skills/actions/runs/44273784957)

旧版 [1.3.1 macOS 安装包](Codex-Checklist-1.3.1-macOS.zip) 仍可下载。
