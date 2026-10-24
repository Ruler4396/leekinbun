# leekinbun

通用的个人 skill 安装仓库。每个 skill 一份 Markdown，写给 AI 读的，放在 `skills/<name>/` 下，与具体 Agent 无关；各 Agent 怎么装见下文。

## 目录结构

```
skills/<name>/SKILL.md        # skill 正文（权威版本在这里）
AGENTS.md                     # 可选模板：用户级指令文件，只引入 skill，不含规则副本
```

## 怎么装

通用做法：把 `skills/<name>/` 整个目录复制到目标 Agent 的用户级 skills 目录，保持 `<name>/SKILL.md` 的形状。

| Agent | 用户级 skills 目录 |
| --- | --- |
| ZCode | `~/.agents/skills/` |
| Qoder | `~/.qoder-cn/` |
| Claude Code | `~/.claude/skills/` |

### 只认 skills 目录的 Agent（如 ZCode、Claude Code）

```
~/.agents/skills/<name>/SKILL.md
```

直接复制即可，不需要 `AGENTS.md`。

### 支持 @ 引入的 Agent（如 Qoder）

额外把 `AGENTS.md` 放到用户级目录，形状保持一致：

```
~/.qoder-cn/AGENTS.md
~/.qoder-cn/skills/leekinbun/SKILL.md
```

`AGENTS.md` 里那句 `@./skills/<name>/SKILL.md` 会被展开成正文，注入本机所有项目、所有会话的上下文，包括新开的子会话。相对路径按 `AGENTS.md` 所在目录解析，所以两处文件的相对位置不能改。

## 改规则

只改 `skills/<name>/SKILL.md` 这一份，然后按上文重装。**不要往 `AGENTS.md` 或 Agent 的配置文件里抄规则**——两处各一份必然会漂。

`leekinbun` 正文第八节把这份 skill 自己也写成了状态机（`Drafting` → `Active` → `Reviewing` → `Refactoring`），触发复盘的条件和压测方法都在里面，所以"改进它"本身有流程，不是想改就改。

## 当前状态

`leekinbun`：`Active`（执行中），2026-10-12 起。本机 `~/.agents/skills/leekinbun/SKILL.md`（ZCode）与仓库那份逐字节一致。
