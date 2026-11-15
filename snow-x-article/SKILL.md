---
name: snow-x-article
description: This skill should be used when writing, rewriting, researching, polishing, or packaging long-form X/Twitter articles in Markdown. It preserves the user's voice, applies high-conversion opening hook and action-oriented TOC strategies, supports research and citation management, runs a self-contained anti-AI-writing editorial pass, and produces a final Hexo-compatible long-form Markdown article. Trigger on "X长文", "推特长文", "写长文", "改长文", "重写文章", "生成X长文", or @command://snow-x-article.
---

# Snow X Article

Create publication-ready **long-form articles** in a single canonical format: Hexo-compatible Markdown that doubles as a high-retention, high-bookmark X long-form source. Treat this as an editorial workflow, not a tweet/thread generator.

Core promise:

1. Preserve the user's voice and strongest original lines.
2. Win both timeline clicks (`preview_text`) and bookmarks with battle-tested opening hooks, pre-writing delivery design, and scannable opening TOCs.
3. Research missing facts when needed and keep claims traceable.
4. Convert notes, outlines, or thread-like drafts into natural long-form article paragraphs with in-place deliverables.
5. Apply a self-contained anti-AI-writing pass before final delivery.
6. Produce one clean Hexo-ready Markdown file. No alternative output formats.

## Canonical File Format (mandatory, the only format)

Every article file MUST follow this exact structure:

```markdown
---
title: 文章标题（不写在正文里，先写清交付什么具体东西，少用感叹号与空洞“保姆级”）
date: YYYY-MM-DD 12:00:00
tags: [标签1, 标签2, 标签3]
---

开篇导语第 1 段（直占 X 卡片 preview_text 黄金预览位）：单点排他交付钩子，或反常识实测数据钩子。

开篇导语第 2 段：反常识反转 + 连环点名 4-7 个真实动手才会撞上的具体卡点。

开篇导语第 3 段：亲测踩坑背书 + 预告文内可直接复制带走的现成材料（提示词/话术/清单/入口）。

**目录**

1. 核心收益或决策表前置
2. 前置准备：关键动作·关键动作
3. 主流程实操：具体步骤与交付
4. 疑难杂症：高频报错·兜底解法

<!-- more -->

## 01｜第一个章节标题

正文自然段（提示词代码块、直达链接、对照截图就地贴在对应步骤正下方）。

## 02｜第二个章节标题

正文自然段。

---

## 参考来源（可选）

1. [公开可访问的引用](https://...)
```

Format rules, all mandatory:

- **Front-matter**: `title` holds the article title. `date` is the writing day plus fixed time `12:00:00`. `tags` are 3-5 items derived from the topic, in `[a, b, c]` inline array form.
- **No H1 in body**. The title lives only in front-matter. Never write `# 标题` in the body.
- **No `## X 长文正文` or similar wrapper headings.**
- **Protect X's `preview_text` window**: X long-form cards display `title` plus roughly the first 100-120 characters of body text. Do **not** lead with ceremonial greetings or unnecessary `> 说明` blockquotes that push the hook out of the preview window. Use a 1-line `> 基于 / 实测环境` blockquote above paragraph 1 **only** when omitting version/hardware context would actively mislead readers.
- **Opening intro** sits between front-matter and `<!-- more -->`. It contains the opening hook paragraphs plus (when applicable) the `**目录**` block.
- **Opening `**目录**` block**:
  - **Default trigger**: Include `**目录**` whenever the article has **≥ 4 chapters** or **≥ 2,000 Chinese characters** (all multi-step tutorials, curated lists, and deep breakdowns). Omit only for short essays (< 4 sections) or when the user asks not to include one.
  - **Exact position & syntax**: Place at the end of the opening intro, **immediately above `<!-- more -->`**. Write the header as bold text `**目录**` on its own line (blank line above and below), followed by a `1. 2. 3. ...` ordered list. **Never** use `# 目录`, `## 目录`, or `### 目录`.
- **`<!-- more -->` position is a hard rule**: always immediately before the first `## ` chapter heading (`## 01｜...`). Never move it to tune excerpt length; adjust the intro instead.
- **Chapters are H2 with zero-padded numbering**: `## 01｜标题`, `## 02｜标题`. Use `###` only for sub-steps or sub-cases inside a chapter (`### 2.1 ...`). Never use `## 第一章｜` word-style numbering.
- **References section is always named `## 参考来源`** (never 参考资料 / 参考链接), placed after a `---` divider at the end, optional.
- **Images** use relative paths under the article directory's image folder (for `Obsidian/02-X/` that is `./image/xxx.png`), unless preserving existing user-pasted image links in an edited draft. If a newly planned image does not exist yet, comment it out as `<!-- TODO: 配图缺失 ./image/xxx.png（画面说明） -->` instead of leaving a broken link.

## Opening Hook Logic (开篇钩子设计规范)

Distilled from high-conversion X workflow articles (e.g. [@EianLu](https://x.com/EianLu/status/2118317430665613741), 5.58M views / 1.35% bookmark rate) and empirical breakdowns ([@yangleiocx3](https://x.com/yangleiocx3/status/2121806957120008475)):

1. **第 1 段：抢卡片点击（二选一，直入主题，零寒暄）**
   - **单点排他交付钩子（实操教程 / 工作流首选）**：第一句直接锁定唯一交付目标与成本收益反差，核心承诺加粗：
     `这篇文章只解决一个问题：**怎么靠［具体方案/工作流］，用［更少的钱/更低门槛］，稳稳拿到［具体结果］，并把［核心暗坑］一次填平。**`
   - **反常识实测数据钩子（测评 / 拆解 / 复盘首选）**：第一句直接亮出自己实测或统计出的反直觉数字对比（如：`41 篇标题带感叹号的长文，浏览中位数有 12.5 万，收藏率却只有 0.69%。`），用硬数据打破常识。
2. **第 2 段：反常识反转 + 连环具体卡点点名（留住前 10 秒阅读）**
   - 先戳破“看起来很简单”的错觉（如：`很多人以为用上 X 就是充个会员、装个客户端的事，真自己动手跑一遍就会发现，装工具反而是最简单的一步。`）。
   - 紧接在同一自然段里一口气点出 **4-7 个实操必撞的具体痛点**（真实报错英文、验证码死循环、隐藏价格坑、配置失效、封号雷区）。越具体越能留住目标读者；注意合成连贯自然段，不要拆成一句一行的碎句子，也不要套用“不是…而是…”。
3. **第 3 段：亲测排雷背书 + 可带走附件预告（触发防御性收藏）**
   - 交代这些坑都已亲测跑通，读者遇到的大部分卡点都能直接在文里翻到答案。
   - **明确点名文内附带的现成材料**（如：“改区话术、协作提示词和配置指令我都直接贴在对应步骤里了，复制就能用”），让手机端没空立刻实操的读者先点收藏。

## Pre-Writing Decision & TOC Strategy (写前四格决策与目录生成策略)

Based on empirical analysis of 358 Chinese X long-form articles (median bookmark rate `0.90%`, [@yangleiocx3](https://x.com/yangleiocx3/status/2121806957120008475)), lock in four decisions **before** generating the TOC and drafting chapters:

### 1. 定交付类型 → 决定章节与目录骨架

| 类型 | 实测收藏率基准 | 适用素材 | 章节与目录编排策略 |
|---|---|---|---|
| **清单合集** | **1.24%（最高）** | 手里有一批同类工具、入口、权益、提示词 | 按资源模块或高价值条目直接编排；每项写清「入口在哪 + 拿来干什么」即止，**严禁为凑字数给每个入口硬塞一段背景介绍**。 |
| **实操教程** | **0.95%**（4k-8k 字）<br>**0.87%**（2k 字内） | 自己跑通的完整流程、报错截图、配置参数 | 严格按**读者跟着动手的先后动作顺序**编排：<br>`01` 先算总账 / 核心收益对比表 / 现成决策表（**高价值结论表前置到第 1 章**）<br>`02` 前置门槛与准备材料（用到的材料必须排在操作步之前）<br>`03-0N` 主流程实操（在哪进 → 填什么 → 做完看到什么）<br>末章：高频疑难杂症 / 报错急救包（兜底排雷，方便按报错检索）。 |
| **观点拆解** | **0.75%（偏低）** | 行业观察、经验复盘、方法论思考 | 切忌空谈两千字行业看法让读者空手离开；动笔前必须多追问一层「读者看完能复制/保存带走什么」，尽量提炼出**一张决策表、自检清单或填空模板**并前置或挂入目录。 |

### 2. 定现成附件 → 严格「就地交付」

- 附带可复用材料的长文收藏率（`0.94%`）显著高于无附件长文（`0.66%`）。动笔前至少备好 **1 样可拿走的交付物**：**提示词代码块**、**对比/核对清单**、**挖空填空模板** 或 **直达入口链接**。
- **就地交付原则**：提示词放进独立代码块，入口链接和界面对照截图**直接贴在用到它的那一步正下方**，绝不让读者隔着几段往回找，也绝不在长文里搞“评论区自取”。

### 3. 定开篇 `**目录**` 条目写法 → 短促、有动作、讲交付

生成 `**目录**` 下的 `1. 2. 3. ...` 条目时，遵守三条生成策略：

1. **一一对应但不机械复读**：条目数量、顺序与正文 `## 01｜`～`## 0N｜` 完全一致，但**不要直接照搬二十多字的长 H2 标题**，单条控制在 **8-18 个字**，手机一屏扫完。
2. **写清「干什么动作 / 交什么东西」，禁用空洞学术词**：禁止出现 `背景介绍`、`核心原理`、`深度解析`、`总结与展望` 等毫无信息量的目录词。
3. **优先采用两种高密度句式**：
   - **单点直给型**：`1. 为什么 Google AI Ultra 5x 爆火` / `3. 低价订阅实操：SEAGM 买土区苹果卡`
   - **`模块：子项·子项` 聚合型**（用中文冒号 `：` 搭配间隔号 `·` 浓缩 2-3 个关键实操点）：
     - `2. 校验逻辑与账号准备：新号注册·转区·节点自检`
     - `7. 手机远控访问：防休眠保活·扫码监工`
     - `8. 疑难杂症：二次验证·锁额度·TUN 模式`

### 4. 定标题与篇幅纪律 → 写清交付物，按动作删减

- **标题先写清交什么**：正文 `title` 与聊天输出的 `标题备选` 都要把**读者能拿走的具体东西**摆进标题里（可用底座：`给［谁］用的［具体东西］：［能拿到什么］（附［现成材料］）` 或 `［低成本/反差结果］：［核心方案与全流程交付物］`）。
  - **少用低转化词**：删掉把词拿掉就不知所云的「保姆级教程」（收藏率仅 `0.76%`）、空洞「干货」，以及标题里的感叹号「！」（浏览高但收藏率仅 `0.69%`）。
  - **善用高收藏信号**：若交付物确实免费可领，可如实点明「免费」（收藏率中位 `1.34%`）；也可采用直击卡点的问句标题（`0.95%`）或明确标出「全流程 / 决策表 / 清单 / 提示词」。
- **篇幅跟动作走，不硬抻字数**：`4,000-8,000` 字（`0.95%`）与 `2,000` 字以内（`0.87%`）收藏率接近，有多少实操步骤和交付物就写多长，绝不注水凑万字。

## Publicness Gate (mandatory final check)

The body and 参考来源 MUST NOT contain:

- drive-letter local paths (`D:/`, `G:/`, `C:\`, etc.)
- local-only file names that are not publicly accessible (private logs, local notes)
- private/internal source names, unless the user explicitly asks

Resolution order: map the local reference to its public equivalent (e.g. `D:/UGit/mini-agent/agent.py` → `https://github.com/Andrew-liu/mini-agent/blob/master/agent.py`); if no public equivalent exists, delete the reference. Verify this gate line-by-line before final write.

## Work Materials Go to Chat, Never to File

Do NOT write any of these into the article file:

- 标题备选 (alternative titles)
- 可压缩成短推的版本 (short-tweet version)
- 发布图片顺序 (image publishing order)
- research notes, publishing notes, pre-writing decision sheets, self-scores

Instead, after the final file is written, output in the chat reply:

1. **标题备选**: 3-5 alternative titles (following the deliverable-first, no-empty-`保姆级`/no-`！` title rule).
2. **可压缩成短推的版本**: a short-tweet compression of the article, ready to post.

These are ephemeral working materials. The file stays clean.

## Critical Writing Rules

- Do **not** write in thread style unless explicitly requested.
- Do **not** use one sentence per paragraph as the default.
- Use natural article paragraphs: target 2-5 sentences per paragraph.
- Keep short paragraphs only for emphasis, not as every line.
- Preserve the user's first-person voice and informal style when present.
- Avoid turning the article into a corporate report or academic paper unless explicitly requested.

Bad article layout:

```markdown
我以前以为 RAG 就是向量库。

后来发现不是。

最近我看了一些资料。

所以我改变了看法。
```

Better article layout:

```markdown
我以前以为 RAG 就是向量库，后来发现这个理解太小了。最近重新看了一些资料后，我更愿意把 RAG 理解成一种给 LLM 找上下文的方式，而不是某个固定的数据库方案。
```

## Output Location

When the user provides a target file, edit that file directly.

When no target file is provided and the workspace has an `Obsidian/02-X/` directory, create the article under:

```text
{workspace}/Obsidian/02-X/{标题}_X长文.md
```

If that path is not available, use the current workspace and report the path.

## Checkpoints

### Checkpoint 1 — Outline Approval

Stop and ask for confirmation before drafting the full article when:

- the user asks to write a new long-form article from rough notes
- the topic is broad or research-heavy
- the article structure is unclear
- the output will be longer than 1,500 Chinese characters

Include in the outline for approval: working `title`, `date`, proposed `tags`, **交付类型 + 核心附件（提示词/清单/模板/入口）**, and the proposed **`**目录**` + chapter list**.

Skip this checkpoint only when the user explicitly asks to directly write/rewrite an existing file or provides a complete chapter outline to execute immediately.

### Checkpoint 2 — Destructive Edit / Final Overwrite

Before overwriting an existing Markdown file:

1. Read the whole file (especially checking for recent manual edits or screenshots added by the user).
2. Confirm the output path.
3. Preserve user-authored sections and user-inserted screenshots when doing targeted updates; if rewriting the whole file, state that the file will be overwritten.
4. Keep a concise completion note after writing.

If the user already gave a direct command like "覆盖 / 落地到这个文件 / 重写这个文件", treat that as approval after reading the file.

## Three-Stage Workflow

### Stage 1 — Pre-Writing Decision, Research, Outline, Voice

1. Run the **4-Grid Pre-Writing Decision**:
   - Who is this for and where are they stuck?
   - Deliverable type (`清单合集` / `实操教程` / `观点+附加工具表`)?
   - Concrete takeaway artifact (`提示词` / `清单` / `模板` / `入口`) and which step it sits under?
   - Opening hook angle (`单点排他承诺` vs `反常识实测数据`) and `**目录**` items?
2. Conduct research when needed:
   - use web search / web fetch for current facts
   - read user-provided local files when relevant
   - distinguish verified facts from personal interpretation
   - never cite private/local sources in the reader-facing article
3. Preserve author voice:
   - keep first-person observations and lived details
   - keep rough-but-real phrasing when it improves authenticity
   - improve clarity without replacing the user's personality
4. Manage citations:
   - use light citations; add `## 参考来源` only when the article cites papers, web articles, reports, or claims needing traceability
   - every reference must pass the Publicness Gate

### Stage 2 — Action-Pruning & Anti-AI-Writing Editorial Pass

Mandatory checks before final delivery:

1. **Action-continuity pruning (动作连贯性删减)**: Walk through from the first step. Ask of every background/filler sentence: *"If I delete this, can the reader still do the next action?"* If yes, cut it. Anywhere the reader would have to pause and search externally mid-step, fill the missing link/command/prompt in place.
2. Remove AI-like filler: "值得注意的是" when unnecessary, "在当今快速变化的时代", "让我们深入探讨", generic opening politeness.
3. Break formulaic structures: forced three-part lists, repeated "不是 X，而是 Y" patterns, mechanical setup/reveal, meaningless "从 X 到 Y" framing.
4. Remove marketing / corporate tone: 赋能、至关重要、深刻变革、不断演变的格局、里程碑式; 生态/闭环/抓手 as empty jargon.
5. Avoid dash spam: avoid `——` and overused `—`; use commas, colons, periods, or paragraph breaks instead.
6. Improve paragraph rhythm: merge isolated one-liners into real paragraphs; mix short, medium, long sentences; use headings for structure, not blank-line stacks.
7. Preserve human voice: concrete details over generic summary; keep genuine uncertainty; prefer authentic roughness over polished corporate prose.
8. Score the article after revision:

| Dimension | Meaning | /10 |
|---|---|---|
| Directness | opens with a strong hook and says the point without ceremonial framing | |
| Rhythm | natural paragraph and sentence variation | |
| Trust | concrete steps/data, avoids over-explaining and fake certainty | |
| Human voice | sounds like a real person, not a generated essay | |
| Concision | passes action-continuity pruning, removes filler while keeping deliverables | |

Gate: ≥45/50 ready; 40-44 polish once if easy; <40 revise before finalizing.

### Stage 3 — Final Review and Hexo-Ready Markdown

1. Format compliance (all hard rules):
   - front-matter present and complete (`title` / `date ... 12:00:00` / `tags`)
   - `title` clearly names the deliverable (no empty `保姆级` or `！` clickbait)
   - no H1 in body, no wrapper headings
   - paragraph 1 directly exposes the hook for X `preview_text`
   - `**目录**` (for ≥4 chapters or ≥2,000 chars) sits right above `<!-- more -->`, uses bold `**目录**` + `1..N` concise items (`8-18` chars), and matches `## 01｜`..`## 0N｜` 1-to-1
   - `<!-- more -->` immediately before `## 01｜`
   - chapters numbered `## 01｜` style
   - prompts, links, and screenshots placed in-place right under their corresponding steps
   - references section (if any) named `## 参考来源` after `---`
2. Publicness Gate: scan every line for local paths and private sources; map to public links or delete.
3. Readability: paragraphs read like an article, no walls of text, headings useful.
4. Facts: key claims sourced or framed as opinion; uncertainties marked.
5. Anti-AI-writing: re-run Stage 2 checks after the final edit.
6. Write the file, then output 标题备选 and 短推版本 in chat (never in the file).

## When Editing an Existing Article

1. Read the whole file first and note any manual edits or screenshots added by the user so you never clobber them.
2. Identify the draft type: notes / outline / thread-like draft / article draft / publish-ready.
3. **If the file is in a legacy format** (body H1 title, `> 主题/日期/用途` blockquote meta block, `## X 长文正文` wrapper, 标题备选 / 短推 / 发布图片顺序 blocks in file, `### 01｜` chapter levels, local paths in references), **migrate it to the canonical format automatically as part of the edit** — no separate permission needed:
   - H1 → front-matter `title`; meta block dates → front-matter `date`; 主题 line → `tags`
   - keep only genuinely necessary environment/version meta lines; make sure paragraph 1 gives X `preview_text` a clean hook
   - delete wrapper headings and work blocks (move to chat if freshly useful, otherwise drop)
   - promote `### NN｜` chapters to `## NN｜`; convert word-style chapter numbering to `01｜` style
   - add or sync `**目录**` right above `<!-- more -->` when the article has ≥4 chapters or ≥2,000 chars, and ensure `<!-- more -->` sits immediately before `## 01｜`
   - fix newly added image paths to the article's image folder convention; run the Publicness Gate
4. If chapters are reordered, immediately sync both `### X.Y` subsection numbers and the opening `**目录**` list so numbering never drifts.
5. If it is thread-like, convert it into article paragraphs.
6. Preserve strong original lines and user-inserted screenshots.
7. Write the final Markdown back to the file and run sanity checks.

## When Creating a New Article

1. Run the 4-Grid Pre-Writing Decision (type, takeaway deliverable, title deliverable, action sequence).
2. Draft a deliverable-clear working title.
3. Build an outline including the `**目录**` items (Checkpoint 1 when applicable).
4. Research missing facts.
5. Write the article body in the canonical format (3-part opening hook → `**目录**` → `<!-- more -->` → `## 01｜` chapters with in-place prompts/links).
6. Apply the action-pruning & anti-AI-writing pass.
7. Final review, write file, deliver 标题备选 + 短推版本 in chat.

## Failure Modes & Fallbacks

| Trigger | First response | Final fallback |
|---|---|---|
| Target Markdown file does not exist | Search nearby paths by filename | Ask the user for the correct path; do not create a replacement unless asked |
| User provides only rough notes and no title | Draft a deliverable-clear working title from the thesis | Use `未命名_X长文.md` only if no usable title can be inferred |
| Draft has only opinions and zero takeaway artifacts | Suggest 1 concrete table, checklist, or template to include | Frame honestly as an essay and tighten length rather than padding fluff |
| Web research returns weak or conflicting sources | Mark the claim as unverified and avoid strong wording | Move the claim out of正文 or remove it |
| A local/private source informed the draft | Use it for context only | Map to a public link or delete the reference; never expose local paths |
| Referenced image file does not exist | Search the image folder for a matching file | Comment the reference out with a `<!-- TODO: 配图缺失 -->` note |
| Outline is too broad | Split into 2-4 possible article angles | Trigger Checkpoint 1 and ask which angle to use |
| Article reads like a thread | Merge sentence fragments into natural paragraphs | Re-run readability review before final write |
| Anti-AI-writing score is <40/50 | Rewrite once using Stage 2 checks | Mark `needs human review` in completion note if still <40 |
| Polishing removes the user's voice | Restore first-person details and concrete phrasing | Keep authentic roughness over polished corporate prose |
| Final Markdown exceeds X long-form comfort length | Run action-continuity pruning to cut non-essential background | Keep all copyable prompts/steps; do not split into thread unless user asks |
| Linter reports errors after editing | Fix clear Markdown/path errors | Report unresolved issues without pretending success |

## Anti-Patterns to Avoid

- Writing the title as body H1 (it belongs in front-matter only).
- Wasting line 1 (`preview_text`) on greetings, background throat-clearing, or multi-line meta blocks.
- Writing `# 目录`, `## 目录`, or `### 目录` instead of bold `**目录**` above `<!-- more -->`.
- Copy-pasting 25+ char H2 titles into `**目录**`, or using empty TOC labels like `背景介绍 / 核心原理 / 总结展望`.
- Leaving `**目录**` out of sync after swapping, adding, or deleting chapters.
- Stuffing `title` with exclamation marks `！` or empty `保姆级教程 / 干货` without naming the concrete deliverable.
- Hiding copyable prompts, templates, or entry links at the end or in comments instead of placing them right under the step that uses them.
- Padding curated list items or tutorial steps with background essays just to stretch word count.
- Writing 标题备选 / 短推版本 / 发布图片顺序 into the article file.
- Using `## X 长文正文` or any wrapper heading.
- Moving `<!-- more -->` away from right above `## 01｜`.
- Leaving drive-letter paths or private source names anywhere in the file.
- Turning every sentence into its own paragraph.
- Using generic AI phrases ("本文将深入探讨", "值得注意的是", "不是…而是…", `——` dash spam).
- Over-polishing the user's voice into corporate prose.

## Completion Report

After finishing, report briefly:

```text
已完成：{file_path}
- 格式：Hexo front-matter / 开篇钩子 + 目录 / more 标记 / H2 编号章节
- 交付物：{文内就地提供的提示词 / 清单 / 模板 / 入口}
- 公开性门禁：{通过 / 处理了 N 处}
- 去 AI 味：{score}/50
```

Then provide in chat: 标题备选 (3-5, deliverable-clear) and 可压缩成短推的版本. Keep the final chat response concise. The main deliverable is the Markdown file.
