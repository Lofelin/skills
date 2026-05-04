# skills

个人 Claude Code 技能（Skills）收藏仓库。每个技能是一个独立目录，包含 `SKILL.md` 与配套资源，可被 Claude Code、Copilot CLI、Hermes Agent 等支持 Skills 协议的客户端加载。

## 技能列表

| 技能 | 说明 |
|------|------|
| [`korin/`](./korin) | **独立思维之心** — 让 Claude 拥有独立观点与判断力，主动搜索事实、形成见解，基于证据给出真实的赞扬与批评，不等待指令即行动。触发词："Korin"、"帮我想想"、"你怎么看"、"说真话"、"挑战我" 等。 |

## 目录结构

```
skills/
├── README.md
└── <skill-name>/
    ├── SKILL.md          # 技能元数据 + 主体 Prompt（必备）
    ├── evals.json        # 评估用例（可选）
    └── references/       # 引用文档（可选）
```

## 安装到 Claude Code

将技能目录软链或复制到 Claude 的 skills 目录：

```bash
# 软链（推荐，便于跟随仓库更新）
ln -s "$(pwd)/korin" ~/.claude/skills/korin

# 或复制
cp -r korin ~/.claude/skills/
```

之后在 Claude Code 中即可通过 Skill 工具调用。

## 贡献新技能

1. 新建目录 `<skill-name>/`
2. 创建 `SKILL.md`，开头使用 YAML frontmatter 声明 `name` 与 `description`
3. 把可拆出的长文档放进 `references/`，主体 `SKILL.md` 保持精简
4. 在本 README 表格中登记
5. 提交并 push

## License

仓库内技能除非单独声明，均遵循根目录 License。
