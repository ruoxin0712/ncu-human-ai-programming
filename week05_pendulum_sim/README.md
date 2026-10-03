# 第 5 周 · 单摆阻尼仿真实验（pendulum_sim）

> 课程：**人类与人工智能编程** ｜ 南昌大学（Nanchang University）

## 实验者信息

| 项目 | 内容 |
| :--- | :--- |
| **姓名** | **邓若馨** |
| **学号** | **6108126003** |
| 专业 | 自动化 |
| 课程 | 人类与人工智能编程 |
| 周次 | Week 05 / 全学期共 16 周 |
| 本模块路径 | `week05_pendulum_sim/` |

## 无菌工作区就绪状态

| 检查项 | 状态 | 说明 |
| :--- | :---: | :--- |
| 独立子目录 | ✅ 就绪 | 仓库根目录下专属文件夹 `week05_pendulum_sim/` |
| 实验元数据 | ✅ 就绪 | [`metadata.yaml`](metadata.yaml) 已写入，字段完整 |
| 无菌状态 | ✅ **STERILE** | 目录内无任何实验产物、无缓存、无虚拟环境 |
| Git 基线 | ✅ 已锁定 | 首条提交仅含初始化文件，SHA 见下 |
| 可回退性 | ✅ 可回退 | `git reset --hard <基线SHA>` 可随时清空重做 |
| 实现进度 | ⬜ 未开始 | 代码尚未编写 |

> **「无菌」（sterile）的含义**：本目录在初始化那一刻是空的、干净的，
> 没有历史遗留物。这意味着接下来每一条提交都只对应一次真实的实验改动，
> 不会混入上周的残留文件 —— 也就是所谓的「干净的基线」。

## Git 基线

```
feat(week05): init pendulum experiment workspace
```

该提交是本实验的**起点锚点**，包含且仅包含两个文件：

```
week05_pendulum_sim/
├── README.md        ← 本文件（实验说明 + 实验者信息）
└── metadata.yaml    ← 本周实验元数据
```

回退命令（会丢弃该提交之后的全部改动，谨慎使用）：

```bash
git reset --hard <基线SHA>
```

## 本周目标

- [x] 建立独立的实验子目录，与主仓库其他模块隔离
- [x] 写入实验元数据（物理模型、参数、依赖、验收标准）
- [x] 锁定 Git 基线提交，确认工作区无菌
- [ ] 用 `numpy` + `scipy` 实现单摆数值积分
- [ ] 用 `matplotlib` 绘制 θ(t) 曲线与 (θ, ω) 相图
- [ ] 验证能量守恒：b=0 时 E(t) 应近似恒定
- [ ] 补全实验报告与心得

## 实验内容

研究**非线性阻尼单摆**的运动规律。对应微分方程：

```
d²θ/dt² = -(g/L)·sin(θ) - b·dθ/dt
```

| 符号 | 含义 | 默认值 |
| :--- | :--- | :--- |
| θ | 摆角 | 待填写 |
| g | 重力加速度 | 9.81 m/s² |
| L | 摆长 | 1.0 m |
| b | 阻尼系数 | 0.0（退化为理想单摆） |
| ω | 角速度 | 0.0 rad/s |

观测量：θ(t) 时间序列、总能量 E(t)、相图 (θ, ω) 轨迹。

完整参数与设计意图见 [`metadata.yaml`](metadata.yaml)。

## 计划目录结构

```
week05_pendulum_sim/
├── README.md        ← 本文件
├── metadata.yaml    ← 实验元数据
├── code/            ← 源代码（pendulum.py 等）
├── data/            ← 小体积示例数据
├── images/          ← 运行结果截图
└── report.md        ← 实验报告与心得
```

> ⚠️ `data/raw/`、`data/cache/`、`outputs/`、`results/` 已被仓库根目录的
> `.gitignore` 排除，实验中间产物不会污染提交历史。

## 运行方式

```bash
cd D:\ncu-human-ai-programming
cd week05_pendulum_sim
python code/pendulum.py
```

> ℹ️ 本机 `python3` 不可用（Windows 应用商店占位存根），**请一律使用 `python`**。

## 实验报告 / 心得

_待完成_