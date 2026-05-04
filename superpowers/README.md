# superpowers-zh 安装说明

> 本目录**不包含** superpowers-zh 源码，仅提供安装方法。
> 上游仓库（作者 [@jnMetaCode](https://github.com/jnMetaCode)）：
> <https://github.com/jnMetaCode/superpowers-zh>

`superpowers-zh` 是 [Anthropic Superpowers](https://github.com/anthropics/skills) 的中文增强版：**20 个 skills**（14 个翻译 + 6 个中国原创），支持 Claude Code / Hermes Agent / Cursor / Claw Code 等 17 款工具。

包含的 skills 例如：`brainstorming`、`writing-plans`、`executing-plans`、`test-driven-development`、`systematic-debugging`、`requesting-code-review`、`receiving-code-review`、`mcp-builder`、`chinese-code-review`、`chinese-commit-conventions`、`chinese-documentation`、`chinese-git-workflow` 等。

---

## 一、Claude Code 安装（推荐：通过 marketplace）

Claude Code 0.3.0+ 内置插件市场，最干净的安装方式。

### 方式 A — 添加 marketplace 后安装插件

```bash
# 在 Claude Code 会话内运行（注意是斜杠命令，不是 shell）
/plugin marketplace add jnMetaCode/superpowers-zh
/plugin install superpowers-zh@superpowers-zh
```

第一行把上游仓库作为 marketplace 注册到 `~/.claude/plugins/marketplaces/`，第二行从中安装 `superpowers-zh` 插件本体到 `~/.claude/plugins/cache/`。

### 方式 B — 一行直接装

```bash
/plugin install superpowers-zh@jnMetaCode/superpowers-zh
```

### 验证安装

```bash
/plugin list
```

应能看到 `superpowers-zh` 处于 enabled 状态。新会话启动后，技能列表里会出现 `superpowers-zh:*` 形式的命名空间（如 `superpowers-zh:brainstorming`）。

### 升级与卸载

```bash
/plugin update superpowers-zh
/plugin uninstall superpowers-zh
```

---

## 二、手动安装（无 plugin 命令时的兜底）

适用于老版 Claude Code、Hermes、Cursor 等不走 marketplace 的环境。

```bash
# 1. 克隆到全局插件目录
git clone https://github.com/jnMetaCode/superpowers-zh.git \
  ~/.claude/plugins/marketplaces/superpowers-zh

# 2. 在 settings.json 中启用（路径示例）
#    macOS / Linux: ~/.claude/settings.json
#    在 plugins 字段加入对应条目，参考上游仓库 README
```

具体 `settings.json` 结构请以上游 README 为准：<https://github.com/jnMetaCode/superpowers-zh#readme>

---

## 三、跨平台说明

| 客户端 | 安装方式 |
|--------|---------|
| **Claude Code** | `/plugin install`（首选） |
| **Hermes Agent** | `skill_view` 自动从 `~/.claude/plugins/` 发现 |
| **Cursor / Claw Code** | 参考上游 `README.md` 中的对应章节 |
| **Gemini CLI** | 通过 `gemini-extension.json` 接入（仓库已含） |
| **Copilot CLI** | 通过 `package.json` 注册 skill 工具 |

---

## 四、使用提示

- **首次进入会话**会自动加载 `using-superpowers` 入口技能；它要求"在任何响应前先调用相关 skill"。
- **命名空间**：所有 skill 以 `superpowers-zh:` 前缀出现，避免与原版 `superpowers:*` 或本地同名 skill 冲突。
- **优先级**：用户的 `CLAUDE.md` > superpowers-zh 技能 > 默认系统提示。详见技能内说明。
- **中国特色路由**：在使用 Gitee / Coding / 极狐 GitLab、写中文 commit、中文文档时，会自动叠加 `chinese-*` 系列。

---

## 五、问题反馈

- 上游 issue：<https://github.com/jnMetaCode/superpowers-zh/issues>
- 本目录仅维护安装说明，不接受功能反馈。
