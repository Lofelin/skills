# skills

个人 Claude Code 技能（Skills）与 Slash Command 收藏仓库。每项资源是一个独立目录或单文件，可被 Claude Code、Copilot CLI、Hermes Agent 等客户端加载。

## 技能列表（Skills）

| 技能 | 说明 |
|------|------|
| [`korin/`](./korin) | **独立思维之心** — 让 Claude 拥有独立观点与判断力，主动搜索事实、形成见解，基于证据给出真实的赞扬与批评，不等待指令即行动。触发词："Korin"、"帮我想想"、"你怎么看"、"说真话"、"挑战我" 等。 |
| [`feishu-doc/`](./feishu-doc) | **产研飞书文档** — 按团队规范生成 PRD / 技术方案 / 设计文档 / 项目复盘：数字编号标题、版本历史表格、统一术语（RD/PM/UX/PoC）、阶段规划不含时间预估。依赖 `feishu-mcp` 工具。 |
| [`superpowers/`](./superpowers) | **superpowers-zh 安装说明**（仅安装指引，不含源码）— 第三方插件 [`jnMetaCode/superpowers-zh`](https://github.com/jnMetaCode/superpowers-zh) 的安装与跨平台接入文档。 |

## Slash 命令（Commands）

| 命令 | 说明 |
|------|------|
| [`commands/commit-as-prompt.md`](./commands/commit-as-prompt.md) | **`/commit-as-prompt`** — 把 Git 提交转化为可被其他 AI 引用的上下文 Prompt：按 WHAT / WHY / HOW 结构化拆分提交，并按 `<Context>` 模板聚合输出。 |

## 目录结构

```
skills/
├── README.md
├── <skill-name>/                # Skill：含 SKILL.md
│   ├── SKILL.md
│   ├── evals.json               # 可选
│   └── references/              # 可选
└── commands/                    # Slash Command：单文件 .md
    └── <name>.md
```

## 安装到 Claude Code

**Skill** — 软链或复制到 `~/.claude/skills/`：

```bash
# 软链（推荐，便于跟随仓库更新）
ln -s "$(pwd)/korin"      ~/.claude/skills/korin
ln -s "$(pwd)/feishu-doc" ~/.claude/skills/feishu-doc
```

**Slash Command** — 软链或复制到 `~/.claude/commands/`：

```bash
ln -s "$(pwd)/commands/commit-as-prompt.md" ~/.claude/commands/commit-as-prompt.md
```

之后在 Claude Code 中即可通过 Skill 工具或 `/commit-as-prompt` 调用。

## 贡献新技能

1. 新建目录 `<skill-name>/`
2. 创建 `SKILL.md`，开头使用 YAML frontmatter 声明 `name` 与 `description`
3. 把可拆出的长文档放进 `references/`，主体 `SKILL.md` 保持精简
4. 在本 README 表格中登记
5. 提交并 push

## License

仓库内技能除非单独声明，均遵循根目录 License。
