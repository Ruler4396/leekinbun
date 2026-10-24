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

每次修订以 commit 为版本（v3 → v3.1 → …），改完同步 `SKILL.md` 头部的版本号与日期，并重装本机各 Agent 的副本。

## 当前状态

`leekinbun`：`Active`（执行中），2026-10-12 起，当前版本 v3.3。本机 ZCode（`~/.agents/skills/`）与 Qoder（`~/.qoder-cn/`）两份副本均与仓库逐字节一致。

v3.3（2026-10-24）：在 v3.1 基础上压缩解释性内容（约 5000 字 → 约 3200 字，物件级约束不变），补充受限环境等价验证，收紧回归锁与视觉债的定义边界。改动经 40 次盲评对照实验验证：20 次 v3.1 vs 瘦身版（产出物指标零损失），20 次 v3.3 vs 无 skill 基线（基线均值 2.0/1.2 vs skill 版 5.0/4.2，工程深度持平、纪律产出物全部来自 skill）。
