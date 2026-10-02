# 第 1 周 · Week 01

> 课程：**人类与人工智能编程** ｜ 南昌大学（Nanchang University）

| 项目 | 内容 |
| :--- | :--- |
| 周次 | Week 01 / 全学期共 16 周 |
| 主题 | 环境搭建、Git 与 GitHub 入门、建立个人作品集主仓库 |
| 日期 | 2026-10-02 |
| 状态 | ✅ 已完成 |

## 本周目标

- [x] 在 Windows 上安装 Git（无需管理员权限）
- [x] 注册 GitHub 账号并创建一个**公开**仓库
- [x] 理解 Git 的基本概念：仓库 / 提交 / 分支 / 远程
- [x] 完成首次提交并成功推送到 GitHub
- [x] 建立覆盖全学期 16 周的作品集目录结构
- [x] 确认 Python 3.12.5 可用，跑通人生第一个程序
- [x] 确认 VS Code 1.139.1 可用

## 实验 / 作业内容

本周没有编程作业，重点是**把工具和仓库准备好**。完成的事：

1. **安装 Git**
   - `winget` 下载失败（`0x80072efd`），改用镜像源下载安装包手动安装
   - 用户级安装，无需管理员权限，避免了权限问题

2. **创建公开仓库**
   - 仓库名：`ncu-human-ai-programming`
   - 地址：https://github.com/ruoxin0712/ncu-human-ai-programming

3. **建立目录结构**
   - `labs/week01 ~ week16`：16 个周次的实验与作业
   - `notes/` `projects/` `docs/` `resources/`：笔记、项目、总结、资料

4. **解决一个意外问题**
   - 当前网络封锁 `github.com`，无法直接 `push`
   - 改用 GitHub 官方 API 通道完成上传，并把本地与远端的提交 SHA 对齐
   - 后续配置 SSH 密钥，恢复了正常的 `git push`（实测连续 6 次推送全部成功）

5. **配置 Python 与 VS Code**
   - 检查发现两者本机均已安装（Python 3.12.5 / VS Code 1.139.1），无需重复安装
   - 设置 `PYTHONUTF8=1`，让 Python 的文件读写统一使用 UTF-8，与 GitHub 保持一致
   - 编写并运行第一个程序 `code/first_program.py`，确认工具链完整可用

## 运行方式

本周唯一的代码是环境验证程序，在**项目根目录**下执行：

```bash
cd D:\ncu-human-ai-programming
python labs/week01/code/first_program.py
```

程序会打印一张迎新卡片，然后等待你输入本学期的目标并给出回应。

日常使用的三条命令：

```bash
cd D:\ncu-human-ai-programming

git add .                                   # 把改动放进"暂存区"
git commit -m "说明：这次改了什么"           # 存档成一次提交
git push                                    # 上传到 GitHub
```

## 第一个程序用到的 5 个概念

文件：[`code/first_program.py`](code/first_program.py)

| # | 概念 | 说明 | 代码位置 |
| :---: | :--- | :--- | :--- |
| 1 | 变量 | 给数据起名字，之后反复使用 | `name = "邓若馨"` |
| 2 | 输出 | 把内容显示到屏幕，用 f-string 嵌入变量 | `print(f"姓名：{name}")` |
| 3 | 计算 | 算术运算与数学一致，乘法用 `*` | `total_hours = weeks * hours_per_week` |
| 4 | 输入 | 用 `input()` 等待用户输入 | `goal = input("请输入…")` |
| 5 | 判断 | 用 `if / elif / else` 做分支，**注意冒号和缩进** | `if total_hours >= 30:` |

> ⚠️ Python 用**缩进**表示代码块。缩进不对会直接报错，这是新手最常见的错误来源。

## 环境信息

| 项目 | 版本 / 路径 |
| :--- | :--- |
| Python | 3.12.5（`python` 与 `py` 均可调用） |
| pip | 24.2 |
| VS Code | 1.139.1 |
| 字符编码 | 已设 `PYTHONUTF8=1`，让 Python 文件读写统一用 UTF-8，与 GitHub 一致 |

> ℹ️ 本机 `python3` 命令不可用（Windows 应用商店的占位存根导致）。**请一律使用 `python`**，功能完全一样。

## 实验报告 / 心得

### 本周理解的几个概念

**仓库（Repository）**
装着全部文件的文件夹，外面套了个"罩子"。设为公开后，任何人不用登录都能打开，
所以它同时也是一个可以写进简历的作品链接。

**提交（Commit）**
给代码拍一张快照，并写一句说明。快照的身份证号叫 SHA，由内容算出 ——
内容差一个空格，号码就完全不同。

**分支（Branch）**
`main` 是主线，保存当前最新、最能跑通的版本。

**公开 / 私有**
作品集必须设为公开，否则别人点不进去，等于没做。

### 踩到的坑

1. **下载 Git 失败** —— `winget` 报网络错误。换镜像源手动下载解决。

2. **16 个周报文件带 UTF-8 BOM**
   BOM 会让 Markdown 开头多出不可见字符。已经剥离，并把行尾统一为 LF。

3. **Git 自带的 SSH 读不了中文用户名路径**
   推送时报 `Host key verification failed`，看着像密钥没配好，实际是 Git 自带的
   SSH 无法正确处理 `C:\Users\禾唯` 这个路径。解决方式：
   ```bash
   git config --global core.sshCommand "C:/WINDOWS/System32/OpenSSH/ssh.exe"
   ```

4. **SSH 连的是 22 端口而不是设定的 443**
   同上原因 —— 配置文件根本没被读到，于是走了默认端口。

### 下周计划

- [ ] 学习 Python 基础语法与数据结构（变量类型、列表、字典）
- [ ] 学会用条件判断和循环写小程序
- [ ] 在 `labs/week02/` 记录第一次实验
- [ ] 熟悉 VS Code 的基本使用（编辑、运行、终端）
