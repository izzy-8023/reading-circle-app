# 读书会 App：项目启动文档

> 状态：概念 / V0.1  
> 用途：作为 Codex 开始产品设计与开发时的项目上下文  
> 核心原则：**Bring your own book. We bring you the people.（带上你的书，我们帮你找到一起读的人。）**

## 1. 产品想法

这是一个围绕“**同一本书**”连接陌生读者的社交阅读 App。

用户不需要先认识其他人，也不需要先加入一个长期存在的读书会。用户首先选择自己想读的一本书，平台寻找在相近时间也想读这本书的人，把他们组成一个小规模、临时的 **Reading Circle（共读小组）**。

核心需求：

- 找到正在读 / 准备读同一本书的人
- 互相督促，提高读完一本书的概率
- 获得“有人和我一起读”的陪伴感
- 围绕具体章节、阅读位置、划线和想法交流
- 尽量避免剧透
- 不要求成员现实中认识
- 不要求所有人完全同步阅读

产品不是传统“建立一个长期 Book Club，再决定读什么书”的模式，而是：

**Book → Match → Reading Circle → Read → Discuss → Finish Together**

---

## 2. 核心产品假设

用户真正需要的可能不是另一个 Goodreads、电子书商店或微信群，而是：

> “我现在想读这本书，但不想一个人读。帮我找到几个也准备读它的人。”

因此，“书”本身就是 matchmaking pool。

示例：

1. 用户搜索《卡拉马佐夫兄弟》
2. 点击「找人一起读」
3. 选择偏好：
   - 开始时间：本周
   - 阅读周期：6 周
   - 阅读速度：慢 / 中 / 快
   - 讨论深度：轻松 / 普通 / 深度
   - 阅读语言
   - 剧透偏好
4. 系统匹配约 4–6 名读者
5. 自动建立一个 Reading Circle
6. 成员独立阅读并更新进度
7. 在章节 / 阅读位置留下想法、划线、问题
8. 其他成员读到相应位置后再看到内容
9. 大家完成整本书
10. Reading Circle 完成生命周期，可选择保持联系或寻找下一本书

---

## 3. 与传统 Book Club 的区别

传统 Book Club 通常是：

**People → Club → Choose Book → Meeting**

本产品希望反过来：

**Book → People → Temporary Circle → Finish Book**

Reading Circle 默认不是永久社区，而是围绕一本书形成的临时关系。

完成后可以显示类似：

> You finished together  
> 18 days  
> 5 readers  
> 127 highlights  
> 46 discussions

然后用户可以：

- 保持联系
- 和部分成员继续读下一本书
- 回到书籍池寻找新的 Reading Circle

---

## 4. Reading Circle 人数

目前初步建议：

**4–6 人为默认值。**

原因：

- 2 人：其中一个退出，共读关系容易直接崩溃
- 20+ 人：容易退化成普通论坛 / 大群，大量潜水
- 4–6 人：既有一定容错，又容易形成“小团队”的存在感

这不是最终决定，需要真实用户测试。

可考虑允许不同模式：

- Buddy Read：2 人
- Reading Circle：4–6 人
- Open Circle：更大的公开讨论

V0.1 优先测试 Reading Circle。

---

## 5. 阅读不应该被强制同步

不要要求：

> “所有人今天必须读到第 83 页。”

更适合：

> 本周目标：Chapter 1–4  
> 5 / 6 人已完成

允许不同成员存在一定进度差。

产品提供的是：

- accountability
- companionship
- awareness

而不是制造阅读压力。

---

## 6. “书本身成为社交界面”

产品不应该只是：

**电子书 + 群聊**

更有价值的体验是让交流附着在阅读过程本身。

例如：

用户读到 Chapter 4，在某个位置留下：

> “这里为什么突然改变叙事视角？”

另一个成员还在 Chapter 2。

此时不显示这条内容。

等对方读到 Chapter 4 / 对应位置后：

> “3 位共读伙伴在这里留下了内容。”

这样产生一种：

**“有人之前从这里经过。”**

的异步共同阅读体验。

这是目前最重要的产品设计方向之一。

---

## 7. 防剧透机制

讨论内容应该和阅读进度绑定。

可能的规则：

- 用户只能默认看到自己已经读到位置之前的讨论
- 后续章节内容隐藏
- 用户可以主动选择「显示剧透」
- annotation / reaction 与 chapter / location 关联

因此：

**Progress 不只是统计功能，也是内容权限的一部分。**

---

## 8. Bring Your Own Book（BYOB）

平台第一阶段不应该成为电子书发行商。

核心原则：

> **你的书属于你，我们负责连接一起读书的人。**

用户可以通过不同方式阅读：

- EPUB
- PDF
- Kindle
- Kobo
- 纸质书
- 图书馆借阅
- 其他电子书平台

Reading Circle 的成员不要求拥有完全相同的文件或版本。

例如：

- A：英文 EPUB
- B：中文版纸质书
- C：Kindle 英文版
- D：PDF
- E：Kobo

系统需要统一的是：

**Work / Book Identity → Edition → Chapter → Approximate Progress**

而不是统一 Book File。

---

## 9. EPUB / PDF 的潜在方案

未来可以允许用户导入自己拥有的 EPUB / PDF。

优先考虑：

**尽可能在用户设备本地解析，而不是永久上传完整书籍到服务器。**

例如本地处理：

- EPUB 文件
- 全文
- 阅读页面
- 本地阅读位置

服务器主要保存：

- book_id
- edition_id
- user_id
- chapter_id
- progress
- 用户主动分享的 highlight
- annotation
- discussion

原则：

**Local = Book**  
**Cloud = People / Social Graph / Progress / Shared Annotations**

注意：本地处理并不自动消除版权法律问题，上线前仍需专业法律审核。

---

## 10. 明确禁止的第一版模式

不要做：

> 用户 A 上传一本商业 EPUB → Reading Circle 其他成员可以直接下载 / 阅读这本完整 EPUB。

这是高风险设计。

也不要在 V0.1：

- 建完整电子书商店
- 大规模托管版权书籍全文
- 试图成为 Kindle / Kobo 替代品
- 一开始就和出版社建立复杂授权体系

---

## 11. 划线 / Annotation

第一版即使没有完整 EPUB Reader，也可以支持类似体验。

### 纸质书 / Kindle / Kobo 用户

用户可以：

1. 选择 Chapter
2. 输入短书摘（可选）
3. 输入页码（可选）
4. 写自己的想法
5. 发布给 Reading Circle

数据结构大致：

**Book → Edition → Chapter → User Quote → Annotation → Discussion**

重点不是建立完整的：

**Book → Copyrighted Full Text**

数据库。

---

## 12. 版权原则（产品层面）

目前讨论得到的基本策略：

### 相对低风险

- 保存书籍 metadata
- ISBN
- 作者
- 封面（仍需使用合法数据源 / API）
- 用户阅读进度
- 用户自己的评论
- Reading Circle
- 阅读目标
- 章节讨论
- 用户主动分享的有限书摘 + 评论

### 风险显著增加

- 平台直接提供完整商业电子书
- 用户上传一本 EPUB 后让其他成员阅读 / 下载
- 大量保存和展示受版权保护正文
- 把用户上传机制事实上变成文件分享服务

正式上线前应由相关司法辖区的版权 / 数字平台律师审核。

---

## 13. 竞品

目前已识别：

### Fable

特点：

- Book Clubs
- 内置电子书
- highlights
- notes
- Social Mode
- Club 成员之间可以围绕文本互动

它更接近：

**Licensed Books + Social Reading**

商业电子书通过正规出版 / 发行渠道提供。

### The StoryGraph

这是目前尤其需要关注的竞品。

Buddy Reads 已涉及：

- 同一本书
- 小规模共同阅读
- 阅读进度
- 防剧透 reaction / discussion
- 推荐可能一起读书的人

因此，仅仅做：

> “同一本书 + 找人 + 进度 + 讨论”

差异化可能不足。

### Bookclubs

更接近：

**Book Club Management Infrastructure**

核心逻辑：

**已有一群人 → 建 Club → 选书 → 安排活动 / 讨论**

和本项目的 Book-first matchmaking 有明显产品逻辑差异。

### READO / Tome / ReadRats 等

分别涉及：

- Social Reading
- 按页 / 章节讨论
- Buddy Reading
- Reading Challenge
- Accountability
- Progress Tracking

需要后续进一步系统化竞品分析。

---

## 14. “是不是抄袭”的原则

类似功能本身通常不是问题。

行业通用功能可以包括：

- 创建 / 加入小组
- 阅读进度
- 评论
- 讨论
- 阅读提醒
- 成员列表
- 阅读目标

但不要直接复制竞品的：

- 源代码
- UI 视觉资产
- 插画
- 图标
- 独特文案
- 商标 / Logo
- 高度特异的整体视觉表达

本项目应该建立自己的用户流程和视觉语言。

---

## 15. 当前可能的核心差异化

需要验证，而不是假设已经成立。

### A. Book-first matchmaking

不是：

> Find a Book Club.

而是：

> Tell us what you want to read.  
> We'll find the people.

### B. 临时 Reading Circle

围绕“一本书”形成，有明确开始和结束。

### C. 自动匹配陌生读者

匹配维度未来可以包括：

- Book
- Start time
- Reading pace
- Language
- Time zone
- Discussion depth
- Activity level
- Spoiler preference

### D. BYOB

用户从任何地方获得书。

平台负责共同阅读体验。

### E. 阅读位置就是社交位置

讨论不是独立聊天室里的信息流，而尽可能和：

- chapter
- progress
- highlight
- reading location

绑定。

---

## 16. V0.1 建议

第一版不要做完整电子书阅读器。

目标只验证：

> **陌生人会不会因为同一本书组成一个小组，并因此更愿意持续阅读和交流？**

### 必须有

1. 注册 / 登录
2. 搜索书籍
3. 书籍详情
4. 「找人一起读」
5. 共读偏好
6. Matching
7. Reading Circle
8. 阅读进度
9. Chapter-based discussion
10. Annotation / quote / thought
11. 防剧透
12. Circle completion

### 暂时不要

- 完整 EPUB reader
- PDF reader
- AI Agent
- AI 自动总结
- 推荐算法
- 复杂 gamification
- 视频 / 音频
- 出版社后台
- 电子书商城
- 支付系统
- 大型公开社区
- 复杂 follower system

---

## 17. 初始页面结构

可能的 V0.1：

### 1. Onboarding

说明核心价值：

> Don't read alone.

或类似的原创品牌表达（最终文案待设计）。

### 2. Home

主要入口：

> What do you want to read?

搜索框。

同时展示：

- Currently reading
- Your Reading Circle
- Recently finished

### 3. Book Page

显示：

- 封面
- 书名
- 作者
- 简介
- 当前寻找共读的人数
- 「Find a Reading Circle」

### 4. Match Preferences

选择：

- Start date
- Pace
- Language
- Discussion style

### 5. Matching

寻找相容读者。

### 6. Reading Circle

显示：

- 成员
- 每个人进度
- 本周目标
- 最近讨论
- 自己的进度

### 7. Chapter

显示：

- Chapter progress
- highlights
- thoughts
- questions
- replies

只显示符合当前阅读进度的内容。

### 8. Completion

展示：

- 完成时间
- Circle 成员
- 阅读统计
- highlights
- discussions
- 是否继续保持联系

---

## 18. 技术方向（初步，不是最终架构）

创始人目前没有编程经验，因此技术方案应：

- 简单
- 主流
- AI Coding 友好
- 少运维
- 容易快速迭代

初步可以考虑：

- Frontend：Next.js
- Backend / Database / Auth：Supabase
- Deployment：Vercel
- Book metadata：后续选择合法可靠 API
- Coding workflow：VS Code + Codex / AI-assisted development

不要为了“AI Native”而增加不必要复杂度。

这个项目第一阶段**不需要多 Agent 架构**。

---

## 19. Codex 开发原则

Codex 在开始开发前应该：

1. 先阅读本文档。
2. 不直接开始实现所有功能。
3. 首先建立清晰的信息架构和数据模型。
4. 将 V0.1 拆成小 milestones。
5. 每次只实现一个可测试闭环。
6. 所有关键技术选择解释原因。
7. 避免过度工程。
8. 不引入没有明确必要性的依赖。
9. 涉及版权内容时默认采用最保守的数据设计。
10. 用户没有编程背景，因此所有操作步骤必须清晰、可复制执行。
11. 出现错误时先解释错误，再给具体修复步骤。
12. 不自行扩大 scope。

---

## 20. Codex 下一步任务

**现在不要直接构建完整 App。**

第一阶段请完成：

### Task 1 — 产品结构

基于本文档提出 V0.1 的：

- 用户旅程
- 页面地图
- 核心实体
- MVP scope

### Task 2 — 数据模型

至少考虑：

- User
- Book
- Edition
- ReadingIntent
- MatchPreference
- ReadingCircle
- CircleMember
- ReadingProgress
- Chapter
- Annotation
- Discussion / Reply

说明实体关系。

### Task 3 — Matching MVP

不要一开始做 AI 推荐算法。

设计一个简单、可解释的 rule-based matching：

**same book + compatible start window + language + pace**

并说明如何在用户数量很少的冷启动阶段工作。

### Task 4 — 技术方案

提出最简单可靠的：

**Next.js + Supabase**

项目架构。

然后等待确认，再开始搭建代码。

---

## 21. 当前最需要回答的产品问题

在写大量代码之前，需要逐步验证：

1. 用户真的愿意和陌生人一起读书吗？
2. 用户希望 2 人、4–6 人还是更大的 group？
3. Circle 应该自动开始还是等人数凑齐？
4. 如果有人中途退出怎么办？
5. 不同阅读速度的人如何共存？
6. Reading Circle 应该持续一本书还是可以继续下一本？
7. Discussion 应该以 Chapter、Page、Percentage 还是 Highlight 为坐标？
8. 不同语言 / 版本如何映射阅读位置？
9. 用户为什么不用 StoryGraph Buddy Reads？
10. BYOB Reader 是否真的构成足够强的差异化？
11. 用户最在意的是 accountability、companionship 还是 discussion？
12. 冷启动时一本冷门书只有 1–2 个用户怎么办？

这些问题的答案应该影响开发优先级。

---

## 22. 一句话定义

目前最清晰的内部产品定义：

> **一个通过“正在读同一本书”匹配陌生读者，并让他们组成小规模临时 Reading Circle、一起完成阅读和讨论的社交阅读产品。**

英文方向：

> **Bring your own book. We bring you the people.**

这只是内部定位草案，品牌名和正式 slogan 尚未确定。

---

## 23. 最重要的原则

**不要先做一个功能很多的 App。**

先证明一个闭环：

> 我想读一本书  
> → 找到几个同样想读的人  
> → 我们开始一起读  
> → 我因为他们而继续读  
> → 我在阅读过程中和他们产生交流  
> → 我们一起读完

如果这个体验成立，再扩展电子书阅读器、AI、推荐、出版社合作等功能。
