# Alibaba Java Coding Guidelines — Agent Skill

> 将《Java 开发手册（黄山版）》（v1.7.1）封装为 AI 编程助手可直接执行的 **Java 开发规范约束 skill**：编码前自查、评审时逐项核对、有疑问时查原文。配套官方 PDF → Markdown 自动转录管线，手册可一键追更。

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)

## 这是什么

阿里巴巴官方发布的《Java 开发手册》是 Java 社区集体智慧的结晶，共 **327 条规约**（【强制】193 /【推荐】97 /【参考】37），覆盖：

- **编程规约**：命名风格、常量定义、代码格式、OOP、日期时间、集合、并发、控制语句、注释、前后端、其他
- **异常日志**：错误码、异常处理、日志规约
- **单元测试 / 安全规约**
- **MySQL 数据库**：建表、SQL、索引、ORM
- **工程结构 / 设计规约**

本仓库把手册变成 **AI 可执行的开发规范**：SKILL.md 定义了触发与执行流程，`references/review-checklist.md` 是可勾选的评审清单，`references/java-coding-guidelines.md` 是手册全文（含全部正反例与 78 个 Java 示例代码块），`scripts/update_guidelines.py` 是手册维护管线。

## 安装

### Claude Code

```bash
mkdir -p ~/.claude/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" ~/.claude/skills/alibaba-java-coding-guidelines
```

### Cursor

```bash
# 项目级（推荐）：放入项目根目录
mkdir -p .cursor/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" .cursor/skills/alibaba-java-coding-guidelines

# 或用户级（全局生效）：
mkdir -p ~/.cursor/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" ~/.cursor/skills/alibaba-java-coding-guidelines
```

### OpenCode

```bash
# 项目级：
mkdir -p .opencode/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" .opencode/skills/alibaba-java-coding-guidelines

# 或用户级（全局生效）：
mkdir -p ~/.config/opencode/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" ~/.config/opencode/skills/alibaba-java-coding-guidelines
```

### WorkBuddy（CodeBuddy）

```bash
git clone https://github.com/Castlebin/alibaba-java-coding-guidelines.git
ln -s "$(pwd)/alibaba-java-coding-guidelines" ~/.workbuddy/skills/alibaba-java-coding-guidelines
```

或直接复制目录到 `~/.workbuddy/skills/` 下。安装后，编写/评审 Java 代码时该 skill 会自动触发，作为开发规范约束日常开发。

### Trae（TraeWork）

```bash
# 用户级（全局生效）：
mkdir -p ~/.trae/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" ~/.trae/skills/alibaba-java-coding-guidelines

# 或项目级：
mkdir -p .trae/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" .trae/skills/alibaba-java-coding-guidelines
```

### Qoder（QoderWork）

```bash
# 用户级（全局生效）：
mkdir -p ~/.qoder/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" ~/.qoder/skills/alibaba-java-coding-guidelines

# 或项目级：
mkdir -p .qoder/skills
ln -s "$(pwd)/alibaba-java-coding-guidelines" .qoder/skills/alibaba-java-coding-guidelines
```

### 通用（不依赖具体助手）

```bash
git clone https://github.com/Castlebin/alibaba-java-coding-guidelines.git
```

然后把 `SKILL.md` + `references/` + `scripts/` 作为一个 skill 包接入你的 Agent 环境。

## 使用场景

| 场景 | 行为 |
| --- | --- |
| 写 / 改 Java 代码 | 自动加载评审清单，按改动章节自查命名/OOP/集合/并发/异常/MySQL 等规范 |
| Java code review | 按章节逐项勾选，输出「通过 / 有条件通过 / 不通过」结论 + 违规清单（强制违规阻断合并） |
| 查询规约 | grep 手册全文，正反例与代码示例即时可查；错误码查附3 表格 |
| 手册追更 | 上游发布新版时运行 `scripts/update_guidelines.py`，自动下载官方 PDF 并重新转录 |

## 目录结构

```
alibaba-java-coding-guidelines/
├── SKILL.md                          # skill 入口：触发条件 + 使用流程
├── references/
│   ├── java-coding-guidelines.md     # 手册全文（黄山版 v1.7.1，自动转录产物，勿手改）
│   └── review-checklist.md           # 可勾选评审清单 + 评审结论模板
├── scripts/
│   ├── update_guidelines.py          # 官方 PDF → Markdown 转录管线（下载/提取/重建）
│   └── requirements.txt              # Python 依赖（pymupdf）
├── LICENSE                           # Apache-2.0
└── README.md
```

## 手册维护

```bash
pip install -r scripts/requirements.txt
python3 scripts/update_guidelines.py            # 自动从 alibaba/p3c 下载官方 PDF 并重新生成手册
python3 scripts/update_guidelines.py --pdf /path/to/manual.pdf   # 使用本地 PDF
```

生成的 `references/java-coding-guidelines.md` 即仓库内权威副本；转录如有瑕疵，请修脚本后重新生成，不要手工改正文。

## 开源协议

Apache-2.0。手册内容源自 [alibaba/p3c](https://github.com/alibaba/p3c)（Apache-2.0），本仓库的转录脚本、评审清单、SKILL.md 同协议开源。

## 致谢

- [alibaba/p3c](https://github.com/alibaba/p3c) — 阿里巴巴 Java 开发手册与 P3C 插件
- 手册社区贡献者：手册为 Java 社区开发者集体智慧的结晶

## 相关链接

- 官方 GitBook：https://alibaba.github.io/p3c/
- 官方仓库：https://github.com/alibaba/p3c
- 配套图书《码出高效》：2018 年 9 月云栖大会发布，36 万字详解

## 公共 skill 仓库提交

已在以下社区 skill 仓库发起收录 PR（评审合并后可通过对应渠道发现本 skill）：

| 仓库 | PR |
| --- | --- |
| [BehiSecc/awesome-claude-skills](https://github.com/BehiSecc/awesome-claude-skills)（10k+ stars，开发/安全向） | [PR #642](https://github.com/BehiSecc/awesome-claude-skills/pull/642) |
| [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills)（14k+ stars，社区精选） | [PR #1180](https://github.com/travisvn/awesome-claude-skills/pull/1180) |
| [spencerpauly/awesome-cursor-skills](https://github.com/spencerpauly/awesome-cursor-skills)（700+ stars，Cursor 技能精选） | [PR #57](https://github.com/spencerpauly/awesome-cursor-skills/pull/57) |
| [TheArchitectit/awesome-opencode-skills](https://github.com/TheArchitectit/awesome-opencode-skills)（140+ stars，OpenCode 技能精选） | [PR #6](https://github.com/TheArchitectit/awesome-opencode-skills/pull/6) |
| [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)（73k+ stars，Claude Code/Codex/WorkBuddy 通用技能合集） | [PR #1751](https://github.com/ComposioHQ/awesome-claude-skills/pull/1751) |

> 注 1：travisvn 仓库要求新技能具备一定的社区使用证明（social proof），新仓库可能需积累 star 后合并；欢迎为该仓库点 star 加速收录。
> 注 2：VoltAgent/awesome-agent-skills（32k+ stars）按其贡献规范仅收录有真实社区使用的新技能（"Brand new skills that were just created are not accepted"），待本技能积累使用量后再提交。
> 注 3：WorkBuddy 官方技能市场（codebuddy.ai/skills）暂无公开的第三方提交渠道；WorkBuddy 兼容标准 `SKILL.md`（本技能已按该格式开发，可放入 `~/.workbuddy/skills/` 直接使用），ComposioHQ 收录后 WorkBuddy 用户亦可发现。
