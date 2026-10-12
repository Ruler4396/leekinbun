# leekinbun

我自己的开发习惯。一份 Markdown，写给 AI 读的：从接需求到交付，每个阶段该做什么、什么算做完。

## 目录结构

```
AGENTS.md                    # 只有一行引入，不含规则副本
skills/leekinbun/SKILL.md    # 规则正文（权威版本在这里）
```

## 怎么装

把两个文件放进 Qoder 的用户级目录 `~/.qoder-cn/`，形状保持一致：

```
~/.qoder-cn/AGENTS.md
~/.qoder-cn/skills/leekinbun/SKILL.md
```

`AGENTS.md` 里那句 `@./skills/leekinbun/SKILL.md` 会被展开成正文，注入本机所有项目、所有会话的上下文，包括新开的子会话。相对路径按 `AGENTS.md` 所在目录解析，所以两处文件的相对位置不能改。

## 改规则

改 `skills/leekinbun/SKILL.md` 这一份，然后重装。**不要往 `AGENTS.md` 里抄规则**——两处各一份必然会漂。

正文第八节把这份 skill 自己也写成了状态机（`Drafting` → `Active` → `Reviewing` → `Refactoring`），触发复盘的条件和压测方法都在里面，所以"改进它"本身有流程，不是想改就改。

## 当前状态

`Active`（执行中），2026-10-12 起。本机 `~/.qoder-cn/skills/leekinbun/SKILL.md` 与本仓库那份逐字节一致。
