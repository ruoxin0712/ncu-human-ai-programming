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
   - 后续配置 SSH 密钥，恢复了正常的 `git push`

## 运行方式

本周无代码需要运行。日常使用的三条命令：

```bash
cd D:\ncu-human-ai-programming

git add .                                   # 把改动放进"暂存区"
git commit -m "说明：这次改了什么"           # 存档成一次提交
git push                                    # 上传到 GitHub
```

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

- [ ] 安装 Python 与 VS Code，跑通第一个 `Hello World`
- [ ] 学习 Python 基础语法与数据结构
- [ ] 在 `labs/week02/` 记录第一次实验
