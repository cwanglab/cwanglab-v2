# Kickoff prompt for a session on another machine

Paste the block below as the first message of a Claude Code session started
inside a fresh or updated clone of this repo. It is self-contained: nothing in
it depends on another machine's ~/.claude session archive.

----8<----
cd 到 cwanglab-v2 仓库，先执行 `git pull origin main`，确认 `git log -1` 显示
5aa594a 或更新。然后按顺序读 HANDOFF.md、../CLAUDE.md（如果 Group/ 目录存在）、
DESIGN_AUDIT_2026-07.md 的 P3 表和 "Not to be done" 节、CONSENT_EMAIL.md。

规则：
- 任何事实只以 CV/c_cv2.tex、citations.bib 和 DOI 为准，不以网站本身或记忆为准。
- 配色、字体、信息组织方式不改；每个数字必须能指到来源。
- 改动前后都跑 `hugo --gc --destination <scratch> --cleanDestinationDir` 并对比页数（当前 64）。
- 推送后用 curl 核对线上 URL，不只看本地构建。
- 发现 HANDOFF.md 与仓库不一致时，以仓库为准并更新 HANDOFF.md。

目标：完成 HANDOFF.md §4 待办表中我在这台电脑上能提供材料的项目，
其余项目列出需要我提供什么。开始前先向我确认你读到的 HEAD 和待办项。
----8<----

## Why this works across machines

- `git pull` carries the work and HANDOFF.md; the GitHub remote is the only shared store.
- `~/.claude/projects/` session archives are per-machine. `claude --resume <id>` from
  this machine's session will NOT work on another machine.
- `.claude/` and `../CLAUDE.md` are not in this repo; HANDOFF.md restates the binding rules
  so the other machine does not depend on them.
