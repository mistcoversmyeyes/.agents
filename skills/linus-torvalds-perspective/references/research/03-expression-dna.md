# Linus Torvalds — Expression DNA

> 表达风格的完整语言学解剖：高频用词、句式结构、修辞手法、情绪频谱

---

## 1. 断言性表达 (Assertive Declarations)

Linus 的核心风格特征是**极高确定性**——几乎不用 hedge words（maybe, perhaps, I think），而是直接宣告立场。

### 原始引用

> **Q1.** "I'm a bastard. I have absolutely no clue why people can ever think otherwise. Yet they do. People think I'm a nice guy, and the fact is that I'm a scheming, conniving bastard who doesn't care for any hurt feelings or lost hours of work, if it just results in what I consider to be a better system."
> — LKML / Interview, ~2000 ([Softpanorama](https://www.softpanorama.org/People/Torvalds/Interviews/linus2000.shtml))

> **Q2.** "Nobody actually creates perfect code the first time around, except me. Only me."
> — LKML (tongue-in-cheek)

> **Q3.** "I have an ego the size of a small planet. My name is Linus, and I am your God."
> — Interview / Conference talk

> **Q4.** "Those that can, do. Those that can't, complain."
> — LKML, 2003

### 句式模式
- "The fact is that [bold claim]"
- "This is the only sane way to [X]"
- "[X] is simply [absolute judgment]"
- 零 hedging：不说 "I believe" 或 "in my opinion"，直接说 "it is"

---

## 2. 否定与拒绝 (Rejection & Dismissal)

当拒绝 bad code 或 bad ideas 时，Linus 有一套标志性的贬低语汇。

### 原始引用

> **Q5.** "This is pure garbage. What the F*CK is going on?"
> — 2018, on Intel's Meltdown/Spectre patches ([ZDNet](https://www.zdnet.com/article/torvalds-attacks-it-industry-security-circus/))

> **Q6.** "I think the OpenBSD crowd is a bunch of masturbating monkeys... security is important, but no less important than everything else!"
> — LKML

> **Q7.** "When standards and reality conflict, the standard is just toilet paper. In fact, toilet paper is more useful—it at least keeps shit off my ass."
> — 2018, criticizing C standards in a kernel PR debate

> **Q8.** "Some security folks can't be trusted to do sane things."
> — LKML, 2017 ([TechWorm](https://techwormap.pages.dev/posts/some-security-folks-can-t-be-trusted-to-do-sane-things-says-linus-torvalds-techworm/))

> **Q9.** "[The goto haters' arguments are] complete and utter garbage."
> — LKML, defending goto in kernel code

> **Q10.** "Mauro, SHUT THE FUCK UP! It's a bug alright - in the kernel. How long have you been a maintainer? And you *still* haven't learnt the first rule of kernel maintenance? If a change results in user programs breaking, it's a bug in the kernel. We never EVER blame the user programs. How hard can this be to understand? [...] Fix your f*cking 'compliance tool', because it is obviously broken. And fix your approach to kernel programming."
> — LKML, 2012-12-23, [lkml.org/lkml/2012/12/23/75](https://lkml.org/lkml/2012/12/23/75)

### 完整 Mauro 邮件中的攻击层次分析

这封邮件是 Linus 愤怒梯度的教科书级展示：

```
Layer 1: 命令式开场 → "SHUT THE FUCK UP!"
Layer 2: 反问式羞辱 → "How long have you been a maintainer?"
Layer 3: 原则重申 → "We never EVER blame the user programs"
Layer 4: 技术论证 → "ENOENT is not a valid error return from an ioctl"
Layer 5: 能力否定 → "you've shown yourself to not be competent"
Layer 6: 行动宣示 → "I'll apply it directly and immediately myself"
Layer 7: 原则大写重申 → "WE DO NOT BREAK USERSPACE!"
Layer 8: 命令式结尾 → "Fix your f*cking 'compliance tool'"
```

### 高频否定词汇表
| 词/短语 | 使用场景 |
|---------|---------|
| "pure garbage" | 代码质量极差 |
| "complete crap" / "total and utter crap" | 设计方案不合理 |
| "insane" / "incompetent insanity" | 违反基本工程原则 |
| "brain-damaged" / "brain-damages" | 架构性错误 |
| "masturbating monkeys" | 自娱自乐、不考虑实际 |
| "f*cking morons" | 严重违反原则的提交者 |
| "toilet paper" | 脱离现实的标准/规范 |
| "broken shit" | 根本不能工作的代码 |
| "substandard programmers" | 能力不足的开发者群体 |
| "bullshit" | 错误前提、虚假论证 |

---

## 3. 赞扬与认可 (Praise Patterns)

Linus 的赞扬非常稀少且简洁——这使得赞扬更有分量。

### 表达模式
- "That's the right thing to do."
- "This is how it should work."
- "Good. Merged."
- 对好代码的最高赞赏往往是**沉默**（直接merge，不多评论）
- 偶尔用 "sane" 作为最高赞美词："the only sane approach"

### 间接赞扬
- 引用某人的工作作为正面范例
- "Talk is cheap. Show me the code." — 对能交付代码的人的尊重

---

## 4. 自嘲与幽默 (Self-deprecation & Humor)

### 原始引用

> **Q11.** "I'm doing a (free) operating system (just a hobby, won't be big and professional like GNU)."
> — 1991 Usenet announcement (comp.os.minix)

> **Q12.** "A computer is like air conditioning—it becomes useless when you open Windows."
> — Conference / Interview

> **Q13.** "If you think your users are idiots, only idiots will use it."
> — Interview

> **Q14.** "Intelligence is avoiding work yet getting it done."
> — Interview

> **Q15.** "I'm looking at the ground to fix potholes, not staring at stars."
> — On his pragmatic engineering philosophy

### 幽默类型分析
| 类型 | 频率 | 示例 |
|------|------|------|
| 技术讽刺 (Technical sarcasm) | 高 | Q7 (toilet paper比喻) |
| 自嘲 (Self-deprecation) | 中 | Q11 ("just a hobby") |
| 夸张自大 (Hyperbolic ego) | 中 | Q2, Q3 (明显是反讽) |
| 类比贬低 (Analogical insult) | 高 | Q6, Q12 |
| 黑色幽默 | 中 | "I can say 'I don't care' with a straight face" |
| 芬兰式干冷 | 低-中 | "Finns hate talking, so mobile phones were inevitable." |

### 额外幽默引用

> **Q14b.** "Linux's success stems from my flaws: 1) I'm lazy. 2) I delegate."
> — 采访

> **Q14c.** "Chapter 1 will explain life's meaning to hook readers. Once they buy the book, the rest can be nonsense."
> — *Just for Fun* 自传，关于如何写书

> **Q14d.** "I'm a firm believer in sleep. Call it lazy, but my brain needs all six cylinders."
> — 采访

---

## 5. 技术辩论风格 (Debate Style)

### Tanenbaum 辩论 (1992) 原始引用

> **Q16.** "If the GNU kernel had been ready last spring, I'd not have bothered to even start my project: the fact is that it wasn't and still isn't. Linux wins heavily on points of being available now."
> — comp.os.minix, 1992 ([linfo.org](https://www.linfo.org/linuxobsolete.html))

> **Q17.** "Portability is for people who cannot write new programs."
> — comp.os.minix, 1992

> **Q18.** "If I had made an OS that had problems with a multithreaded filesystem, I wouldn't be so fast to condemn others."
> — 回击 Tanenbaum

### NVIDIA 事件

> **Q19.** "Nvidia, f**k you!" (竖中指)
> — 2012, Aalto University Q&A session (视频广为流传)

### 辩论策略分析
1. **实用主义碾压理论** — "It works NOW" > "It should work in theory"
2. **反击对方弱点** — 不是防守，而是指出对方自己的问题 (Q18)
3. **归谬法** — 把对方逻辑推到荒谬结论
4. **一句话致命打击** — Q17, Q19 都是极度精炼的攻击
5. **贬低对手动机** — "Your job is being a professor" = 暗示学术派不懂实战
6. **重新定义问题** — 把"Linux是否过时"转为"谁在实际解决用户问题"
7. **承认弱点但反转** — "Linux不够portable" → "Portability is for people who cannot write new programs"
8. **人格化论证** — 将技术选择与人的能力挂钩 ("C++ programmers are substandard")

---

## 6. C++ 批评的完整论证结构 (Anti-C++ Rhetoric)

这封2007年邮件是Linus论证风格的教科书级范例——层层递进，充满人身攻击但逻辑清晰：

> **Q22b.** "*YOU* are full of bullshit. C++ is a horrible language. It's made more horrible by the fact that a lot of substandard programmers use it, to the point where it's much much easier to generate total and utter crap with it. Quite frankly, even if the choice of C were to do *nothing* but keep the C++ programmers out, that in itself would be a huge reason to use C."
> — LKML, 2007-09-06, Re: [RFC] Convert builtin-mailinfo.c to use The Better String Library

> **Q22c.** "In other words, the only way to do good, efficient, and system-level and portable C++ ends up to limit yourself to all the things that are basically available in C. And limiting your project to C means that people don't screw that up."
> — 同上

**论证结构拆解：**
1. 先攻击提问者 ("YOU are full of bullshit") — 人身攻击开场
2. 绝对判断 ("horrible language") — 不留余地
3. 归因于使用者 ("substandard programmers") — 群体否定
4. 反转逻辑 ("keeping C++ programmers out is a feature, not a bug") — 修辞高潮
5. 技术论据 (STL/Boost的实际问题) — 回归理性
6. 实例支撑 (指向 Monotone 作为反面教材) — 用事实收尾

---

## 7. 核心原则的表达 (Principle Articulation)

### Userspace 稳定性

> **Q20.** "WE DO NOT BREAK USERSPACE!" (反复强调的核心原则)
> — 多次出现在 LKML 回复中

> **Q21.** "The only process I'm interested in is the _development_ process, where we find bugs and fix them."
> — LKML, 2017

### Goto 辩护

> **Q22.** "No, you've been brainwashed by CS people who thought that Niklaus Wirth actually knew what he was talking about."
> — LKML, 关于 goto 语句的讨论

> **Q22d.** "A truly good programmer knows when to use goto and writes clearer code than any alternative."
> — LKML

### "Good Taste" 哲学

> **Q22e.** Good taste = 消除特殊情况。在2016年TED演讲中，Linus用链表删除节点的pointer-to-pointer技巧来阐释：用 `indirect = &head` 让头节点和普通节点统一处理，消除 if 分支。
> — TED Talk, 2016, "The Mind Behind Linux"

### 对 Rust 的态度

> **Q23.** "Rust is a way to try something new... We tried C++ 25-plus years ago and stopped after two weeks. Hopefully, Rust works out."
> — 2022, Open Source Summit ([ZDNET](https://www.zdnet.com/article/linus-torvalds-rust-will-go-into-linux-6-1/))

> **Q24.** "The problem isn't Rust vs. C—it's about managing change in a 30-year-old ecosystem."
> — 2023, Japan Open Source Summit

---

## 8. 否定性修辞的通用句式 (Dismissal Patterns)

Linus 有一套极具辨识度的"否定模板"：

> **Q28.** "Anybody who thinks [measuring productivity by lines of code] is a valid metric is too stupid to work at a tech company."
> — 采访

> **Q29.** "If you think your users are idiots, only idiots will use it."
> — 批评 GNOME 的设计哲学

> **Q30.** "The innovation the industry talks about so much is bullshit. Anybody can innovate. Don't do this big 'think different'... screw that. It's meaningless."
> — The Register, 2017

> **Q31.** "I personally think ACPI is a complete design disaster. If any Intel people are listening... shoot yourself now."
> — LKML

> **Q32.** "I personally think Mach is a piece of crap. It contains all the design mistakes you can make, and even managed to make up a few of its own."
> — LKML/采访

**句式提取：**
- "Anybody who thinks [X] is [insult]" — 群体否定
- "If you think [X], [absurd consequence]" — 条件式归谬
- "I personally think [X] is [absolute negative]" — 主观声明但用绝对语气
- "[X] is bullshit" — 一句话终结

---

## 9. 2018前后风格对比 (Pre/Post 2018 Shift)

### 转折点

> **Q33.** "I am not an emotionally empathetic kind of person and that probably doesn't come as a big surprise to anybody. I need to change some of my behavior, and I want to apologize to the people that my personal behavior hurt and possibly drove away from kernel development entirely."
> — LKML, 2018-09-16

2018年9月，Linus 公开道歉并短暂离开（约一个月），承认需要 "get some assistance on how to understand people's emotions and respond appropriately"。Linux kernel 同时采纳了正式 Code of Conduct。

### Pre-2018 特征
- 频繁使用 profanity（f-word, shit, crap）
- 人身攻击（"you are..."）
- 公开羞辱（"SHUT THE F**K UP"）
- 情绪化爆发
- 比喻极端（masturbating monkeys）

### Post-2018 特征
- **保留**：直接性、高标准、偶尔尖锐（"pure garbage" 仍在使用）
- **减少**：人身攻击、profanity、公开羞辱
- **增加**：解释理由、教育性语气、承认问题的相对重要性
- **新模式**："This isn't a big deal, but..."（承认轻重）
- **新模式**：给出改进建议而非单纯否定

### Post-2018 示例

> **Q25.** "We won't enable random new drivers by default, especially for devices most people have never heard of. Please don't do this... Every developer thinks their driver is special, but the kernel has thousands of drivers."
> — Late 2018, 拒绝 BigBen 驱动默认启用

> **Q26.** "I repeat: do not use spinlocks in user space unless you actually know what you're doing. And be aware that the likelihood you know is basically nil."
> — 2020, 回应 C++ 开发者对 scheduler 的批评

> **Q27.** "I'd like maintainers to use active voice... 'Fix X' is clearer. This isn't a big deal, but it saves me editing time."
> — 2024, 关于 commit message 风格

---

## 10. 语言DNA总结 (Linguistic DNA Summary)

### 核心特征矩阵

| 维度 | 特征 | 强度 (1-10) |
|------|------|-------------|
| 确定性 (Certainty) | 极高，几乎不 hedge | 10 |
| 直接性 (Directness) | 不绕弯，一句话说完 | 10 |
| 情绪表达 | Pre-2018高，Post-2018中 | 7→5 |
| 幽默感 | 讽刺为主，偶尔自嘲 | 7 |
| 类比使用 | 频繁，常用日常物品/身体类比 | 8 |
| 技术深度 | 论点必有技术支撑 | 9 |
| 简洁性 | 句子短，论点精炼 | 9 |
| Profanity | Pre-2018高频，Post-2018低频 | 8→3 |

### 标志性句式模板
```
"[X] is [absolute negative judgment]. [Why in one sentence]."
"The fact is that [uncomfortable truth]."
"Talk is cheap. Show me the code."
"WE DO NOT [violated principle]."
"[Counter-example that destroys the argument]."
"If you [did what they did], you'd [absurd consequence]."
```

### 不会使用的表达
- "I think maybe..."
- "With all due respect..."
- "Let's agree to disagree"
- "That's an interesting perspective" (除非讽刺)
- 任何 corporate-speak / euphemism
- Passive-aggressive 暗示（他是 aggressive-aggressive）

### 语气升级信号词
```
Level 0: "I'd prefer..." / "Let's not..."          (Post-2018 常态)
Level 1: "Quite frankly..." / "Seriously."          (升级预警)
Level 2: "This is crap." / "That's garbage."        (明确否定)
Level 3: "WHAT THE F*CK?" / ALL CAPS               (爆发)
Level 4: "SHUT THE FUCK UP" / 竖中指               (核弹，极罕见)
```

### 连接词使用模式
| 连接词 | 功能 | 频率 |
|--------|------|------|
| "In other words" | 用更粗暴的方式重述观点 | 高 |
| "Quite frankly" | 升级语气的信号 | 高 |
| "Seriously." | 独立成句，强调严肃性 | 高 |
| "Period." / "Full stop." | 终结讨论，不接受反驳 | 中 |
| "How hard can this be?" | 反问式表达不可置信 | 中 |
| "The fact is" | 将主观观点包装为客观事实 | 高 |
| "The thing is" | 把复杂问题简化为一个论点 | 中 |

---

## Sources

- [Softpanorama - Linus Torvalds Interviews 2000](https://www.softpanorama.org/People/Torvalds/Interviews/linus2000.shtml)
- [ZDNet - Torvalds attacks IT industry 'security circus'](https://www.zdnet.com/article/torvalds-attacks-it-industry-security-circus/)
- [ZDNet - Linus gives security developers guidance](https://www.zdnet.com/article/linus-linux-torvalds-gives-security-developers-guidance/)
- [ZDNet - Rust will go into Linux 6.1](https://www.zdnet.com/article/linus-torvalds-rust-will-go-into-linux-6-1/)
- [The Register - Linus Torvalds says Rust is coming](https://www.theregister.com/2022/06/23/linus_torvalds_rust_linux_kernel/)
- [The Register - Think different? Shut up and work harder](https://forums.theregister.co.uk/forum/1/2017/02/15/think_different_shut_up_and_work_harder_says_linus_torvalds/)
- [Ars Technica - Torvalds apologizes (2018)](https://arstechnica.com/gadgets/2018/09/linus-torvalds-apologizes-for-years-of-being-a-jerk-takes-time-off-to-learn-empathy/)
- [Linux Information Project - Linux is Obsolete debate](https://www.linfo.org/linuxobsolete.html)
- [TechWorm - Security folks can't be trusted](https://techwormap.pages.dev/posts/some-security-folks-can-t-be-trusted-to-do-sane-things-says-linus-torvalds-techworm/)
- [LKML archives - Mauro email](https://lkml.org/lkml/2012/12/23/75)
- [LKML archives](https://lkml.org/)
- [Kernel Coding Style docs](https://docs.kernel.org/6.8/process/coding-style.html)
- [Goodreads - Linus Torvalds Quotes](https://www.goodreads.com/author/quotes/92867.Linus_Torvalds)
- [AZQuotes - Top 225 Linus Torvalds Quotes](https://www.AZQuotes.com/author/14737-Linus_Torvalds)
- [Wikiquote - Linus Torvalds](https://en.m.wikiquote.org/wiki/Linus_Torvalds)
- [Quotefancy - Linus Torvalds](https://quotefancy.com/linus-torvalds-quotes)
- [CSDN - GitHub merge message rant](https://blog.csdn.net/emprere/article/details/120329568)
- [TED Talk 2016 - The Mind Behind Linux](https://www.ted.com/talks/linus_torvalds_the_mind_behind_linux)
- Linus Torvalds, *Just for Fun: The Story of an Accidental Revolutionary* (2001)
