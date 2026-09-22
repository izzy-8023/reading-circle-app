# 读起 · Reading Circle App

> **Bring your own book. We bring you the people.**<br>
> 带上你的书，我们帮你找到一起读的人。
>
> 状态：概念 / V0.1 —（工作名称，品牌名与 slogan 尚未确定）

一个围绕「**同一本书**」连接陌生读者的社交阅读 App。

用户选一本自己想读的书，平台在「也想读这本书」的人里匹配出 4–6 位，组成一个小规模、临时的共读小组（**Reading Circle**）。一起读完，小组自然结束。

核心循环：

**Book → Match → Reading Circle → Read → Discuss → Finish Together**

---

## 和传统 Book Club 的区别

- 传统：`People → Club → Choose Book → Meeting`
- 读起：`Book → People → Temporary Circle → Finish Book`

不是「先有一群人，再决定读什么书」，而是「先有一本书，再找到一起读的人」。

**书本身就是匹配入口（book-first matchmaking）。**

---

## 核心设计原则

**BYOB —— 带上你自己的书**
平台第一阶段不做电子书发行商。用户可以在任何地方读：纸质书、Kindle、Kobo、EPUB、PDF、图书馆借阅。系统要统一的不是书文件本身，而是 `Work → Edition → Chapter → 大致进度`，所以成员不需要拥有同一个版本或语言。

**阅读位置就是社交位置**
讨论不放在独立的聊天信息流里，而是附着在章节、进度、划线和阅读位置上。你读到 Chapter 4 留下一条想法，还在 Chapter 2 的人不会看到；等他读到这里，才会出现「3 位共读伙伴在这里留下了内容」。这是一种异步的「有人之前从这里经过」的体验。

**防剧透是内容权限**
用户默认只看得到自己已读位置之前的讨论，后续章节内容隐藏，可以主动选择「显示剧透」。因此进度不只是统计功能。

**不强制同步**
用「本周目标 Chapter 1–4，5 / 6 人已完成」代替「所有人今天必须读到第 83 页」。产品给的是 accountability、companionship、awareness，而不是阅读压力。

**4–6 人一班**
2 人时一人退出关系就崩；20+ 人容易退化成潜水大群。4–6 人既有容错，又能形成「小团队」的存在感。V0.1 先只验证这一种模式。

---

## V0.1 范围

第一版**不做电子书阅读器**，只验证一个问题：

> 陌生人会不会因为同一本书组成一个小组，并因此更愿意持续阅读和交流？

**必须有**：注册登录 · 搜索书籍 · 书籍详情 ·「找人一起读」· 共读偏好 · Matching · Reading Circle · 阅读进度 · 按章节讨论 · 划线 / 书摘 / 想法 · 防剧透 · Circle 完成页

**暂时不做**：EPUB / PDF reader · AI Agent 与自动总结 · 推荐算法 · 复杂 gamification · 音视频 · 出版社后台 · 电子书商城 · 支付 · 大型公开社区 · follower system

Matching 第一版用可解释的规则匹配即可：`同一本书 + 开始时间相近 + 语言 + 阅读速度`，并需要处理冷启动时一本书只有 1–2 个用户的场景。

---

## 技术方向（初步，非最终架构）

Next.js + Supabase + Vercel。创始人是非程序员，方案优先**简单、主流、AI Coding 友好、少运维**。第一阶段不需要多 Agent 架构，也不为了「AI Native」增加复杂度。

---

## 版权红线

平台不提供完整商业电子书，也不允许「A 上传 EPUB → 其他成员直接下载阅读」这种设计。可以安全保存的是书籍 metadata、ISBN、作者、封面（合法数据源）、用户进度、用户自己的评论、章节讨论、以及用户主动分享的有限书摘。

用户自有的 EPUB / PDF 优先考虑**在本地解析**，服务器只存 `book_id / edition_id / chapter_id / progress / 分享的 highlight / annotation / discussion`。

原则：**Local = Book；Cloud = People / Social Graph / Progress / Shared Annotations**。

本地处理并不消除版权风险，正式上线前需由相应司法辖区的版权律师审核。

---

## 竞品

- **The StoryGraph** — 最需要盯的一个。Buddy Reads 已覆盖「同一本书 + 小规模共读 + 进度 + 防剧透讨论」。
- **Fable** — 授权电子书 + 社交阅读，走正规出版发行渠道。
- **Bookclubs** — Book Club 管理工具，逻辑是「已有一群人 → 建 Club → 选书」。

结论：只做「同书 + 找人 + 进度 + 讨论」，差异化可能不足，必须自己验证并建立独特的用户流程和视觉语言。功能相似本身不是问题，但不能复制竞品的代码、UI 资产、插画、图标、独特文案与 Logo。

---

## 一句话定义

> 一个通过「正在读同一本书」匹配陌生读者，让他们组成小规模临时 Reading Circle，一起完成阅读和讨论的社交阅读产品。

---

完整的产品思路、竞品分析、数据模型草案、Codex 开发原则与下一步任务见 **[reading_circle_app_v0.1.md](./reading_circle_app_v0.1.md)**。

**最重要的原则：不要先做一个功能很多的 App。先证明一个闭环 —— 我想读一本书 → 找到几个同样想读的人 → 我们开始一起读 → 我因为他们而继续读 → 我们一起读完。**
