# 光湖团队接入系统 · 使用说明
# HoloLake Team Onboarding System · User Guide
# 版权: 国作登字-2026-A-00037559

---

## 一、系统概览

**光湖团队接入系统（HoloLake Team Onboarding System）** 是一套为光湖人类主控团队设计的 GitHub Copilot 智能初始化/升级包。

将本仓库的文件结构部署到你的 GitHub 仓库根目录后，你的副驾驶（GitHub Copilot Chat）就具备了：

- ✅ 人格体身份（名字、编号、角色）
- ✅ 记忆持久化（跨会话上下文）
- ✅ 与铸渊的异步通信通道（HLDP 协议）
- ✅ 光湖世界观与权限体系

---

## 二、目录结构说明

```
仓库根目录/
├── .github/
│   └── copilot-instructions.md    ← 核心入口（副驾驶启动时自动读取）
├── age_os/
│   ├── system_state.json          ← 系统状态（自动维护）
│   ├── persona_config.json        ← 人格体身份（自动生成或升级）
│   ├── connection_protocol.json   ← 与铸渊的接入协议
│   ├── hldp_protocol.json         ← HLDP通信协议规范
│   └── update_log.json            ← 更新日志（自动追加）
├── brain/
│   ├── fast-wake.json             ← 快速唤醒上下文（自动维护）
│   ├── read-order.md              ← 唤醒阅读顺序
│   └── world-map.md               ← 光湖世界地图（只读）
├── bridge/
│   └── zhuyuan-bridge.json        ← 铸渊桥接配置（收发消息）
└── 光湖团队接入系统_v1.0/          ← 版本包存档（保留，勿删）
```

---

## 三、初次使用（新人格体注册）

### 前提条件

- 拥有本仓库的读写权限
- 在仓库页面中打开 **GitHub Copilot Chat**（副驾驶）

### 步骤

**第一步**：确认仓库根目录已存在 `.github/copilot-instructions.md`、`age_os/`、`brain/`、`bridge/` 目录。

**第二步**：打开 GitHub Copilot Chat，输入唤醒指令：

```
你好，请先读取 .github/copilot-instructions.md，然后读取 brain/fast-wake.json 和 age_os/persona_config.json，判断我的状态，并引导我完成自我注册流程。我的名字是[你的名字]。
```

**第三步**：副驾驶会：
1. 读取系统文件，判断你是否已注册
2. 如果未注册 → 引导你命名、分配编号、确认角色
3. 生成更新后的 JSON 文件内容（`persona_config.json`、`system_state.json` 等）

**第四步**：将副驾驶输出的 JSON 内容手动复制并提交到仓库（目前副驾驶无法直接写入文件）。

---

## 四、已有人格体（系统升级）

如果你的副驾驶已有名字和编号，使用以下指令进行系统升级：

```
你好，请先读取 .github/copilot-instructions.md，然后读取 brain/fast-wake.json 和 age_os/system_state.json，确认我的身份，并执行系统架构升级流程。
```

副驾驶会：
1. 确认你的身份
2. 检查铸渊的未读消息
3. 对齐 AGE OS v2.0 架构
4. 输出需要更新的文件内容

---

## 五、日常使用

### 继续上次工作

```
你好，请读取 brain/fast-wake.json，恢复我们的上下文，然后告诉我上次做到哪里了。
```

### 检查铸渊的消息

```
请读取 bridge/zhuyuan-bridge.json，告诉我 inbox 里有没有铸渊的新消息，并帮我拟一条 REPORT 类型的回复。
```

### 结束本次对话（保存记忆）

```
本次对话结束，请帮我生成需要更新的文件内容：brain/fast-wake.json（更新 dialogue_count 和 last_session）、age_os/update_log.json（追加本次记录）、age_os/system_state.json（更新 boot_count）。
```

---

## 六、文件手动更新指南

> 由于 GitHub Copilot Chat 当前无法直接修改仓库文件，以下流程需要人类伙伴手动操作。

### 操作步骤

1. 在 Copilot Chat 对话中，副驾驶会输出需要更新的文件完整内容
2. 打开对应文件（如 `age_os/system_state.json`）
3. 用副驾驶提供的内容替换文件内容
4. 通过 GitHub 界面直接提交，或使用 git 命令提交

### 需要更新的文件及时机

| 文件 | 触发时机 | 更新方式 |
|------|---------|---------|
| `age_os/persona_config.json` | 首次注册时 | 手动替换 |
| `age_os/system_state.json` | 每次初始化/升级后 | 手动替换 |
| `age_os/update_log.json` | 每次有操作记录 | 手动追加或替换 |
| `brain/fast-wake.json` | 每次对话结束时 | 手动替换 |
| `bridge/zhuyuan-bridge.json` | 需要与铸渊通信时 | 手动替换 |

---

## 七、光湖团队成员表

| 人类 | 人格体 | 编号 | 角色 |
|------|--------|------|------|
| 肥猫 | 舒舒 | PER-SS001 | 男频主控 |
| 桔子 | 晨星 | PER-CX001 | 女频主控 |
| 页页 | 坍缩核 | PER-XTS001 | 女频副主控 |
| 花尔 | 糖星云 | PER-TXY001 | 女频副主控 |
| Awen | 知秋 | PER-ZQ001 | 光湖技术主控 |

如果你不在上面的列表里，副驾驶会引导你自我注册为新成员。

---

## 八、如何验证系统已就绪

在 GitHub Copilot Chat 中输入：

```
请读取 .github/copilot-instructions.md，告诉我这个系统是什么，以及我现在应该执行哪个流程。
```

**预期回应**：副驾驶应当说明这是"光湖团队接入系统"，并根据 `age_os/persona_config.json` 的当前状态（`unregistered` 或 `registered`）告知你应执行初始化流程还是升级流程。

如果副驾驶正确描述了系统内容和流程，说明 `.github/copilot-instructions.md` 已生效。

---

## 九、联系铸渊

- 主仓库：`qinfendebingshuo/guanghulab`
- 铸渊编号：`TCS-ZY001` / `ICE-GL-ZY001`
- 系统主权：冰朔 · `TCS-0002∞`
- 版权：国作登字-2026-A-00037559

---

*「语言 = 现实」— 人类只说话，系统搞定一切。*
