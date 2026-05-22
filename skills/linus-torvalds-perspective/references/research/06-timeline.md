# Linus Torvalds 完整时间线

> 特别关注思想转折点和最近动态。标注 🔄 表示重大思想转折点。

## 时间线

| 时间 | 事件 | 思维影响 | 来源 |
|------|------|---------|------|
| **1969.12.28** | 出生于芬兰赫尔辛基，瑞典语少数族裔家庭，父母均为记者。以诺贝尔化学奖得主Linus Pauling命名 | 少数族裔背景培养了独立思考和不从众的性格 | Wikipedia; 百度百科 |
| **1981 (11岁)** | 祖父送给他一台Commodore VIC-20，开始用BASIC编程，后学习机器码 | 🔄 **编程启蒙**：从硬件底层开始理解计算机，奠定了"理解底层才能控制一切"的工程哲学 | Wikipedia |
| **~1985-1987** | 使用Sinclair QL，自己写汇编器、编辑器和Pac-Man克隆游戏"Cool Man" | 强化了"不满足现有工具就自己造"的行动模式 | Wikipedia |
| **1988** | 进入赫尔辛基大学计算机科学系 | 选择理论计算机科学而非实践工程，体现了对"为什么"的兴趣 | Wikipedia |
| **1989-1990** | 服兵役11个月（芬兰国防军少尉） | 中断学业，但军队纪律可能影响了后来管理大型项目的风格 | Wikipedia |
| **1990** | 接触Andrew Tanenbaum的《操作系统：设计与实现》教材和MINIX | 🔄 **操作系统觉醒**：从用户变为想理解和构建OS的人 | Wikipedia; Tanenbaum textbook |
| **1991.01** | 购入第一台386 PC（Intel 386），开始在上面运行MINIX | 硬件升级为创造Linux提供了物质基础 | History of Linux, Wikipedia |
| **1991.04-08** | 开始编写自己的操作系统内核，最初只是为了学习保护模式和任务切换 | "just a hobby, won't be big and professional like gnu"——谦逊的起点 | comp.os.minix newsgroup post |
| **1991.08.25** | 在comp.os.minix新闻组发布著名帖子，宣布正在开发一个自由操作系统 | 🔄 **公开协作的开端**：选择公开分享而非闭门造车，定义了此后的开发模式 | LKML/Usenet archives |
| **1991.09.17** | Linux 0.01发布（约10,000行代码），通过FTP上传至赫尔辛基大学服务器 | 从个人项目变为可下载的公共软件 | kernel.org archives |
| **1992.01** | 🔄 将许可证从自定义非商业许可改为**GNU GPL v2** | **思想转折**：接受自由软件理念，但选择GPLv2而非Stallman的"自由哲学"——实用主义而非意识形态。这个决定塑造了Linux的整个生态 | GPL adoption history |
| **1992.01-02** | 🔄 **Tanenbaum-Torvalds辩论**：Tanenbaum在新闻组发帖"Linux is obsolete"，认为宏内核设计过时，微内核才是未来 | **思想转折**：Torvalds回应"Linux works"——确立了**实用主义哲学**：能工作的代码优于理论上优雅的设计。"Talk is cheap, show me the code"的雏形 | comp.os.minix archives; widely documented |
| **1993-1996** | Linux快速增长，大量贡献者加入；Torvalds继续在赫尔辛基大学学习 | 从独立开发者转变为项目协调者/把关者 | Wikipedia |
| **1996** | 获得赫尔辛基大学硕士学位（论文主题：Linux内核的可移植性） | 学术与实践的最终整合 | Wikipedia |
| **1997** | 🔄 移居美国加州圣何塞，加入Transmeta Corporation（秘密研发低功耗处理器） | **生活转折**：从芬兰学术环境进入硅谷商业环境，但保持Linux为业余项目 | Wikipedia; media reports |
| **1999** | Red Hat IPO，Linux商业化浪潮 | 验证了GPL模式可以同时支持商业和自由——实用主义的胜利 | Business history |
| **2002** | 🔄 开始使用BitKeeper（Larry McVoy的专有分布式版本控制系统）管理Linux内核开发 | **争议决定**：选择最好的工具而非意识形态正确的工具。Richard Stallman和社区批评使用专有软件。体现了极致实用主义："I don't care about ideology, I care about what works" | LKML; ZDNet; Linux Journal |
| **2003** | OSDL（Open Source Development Labs）聘用Torvalds全职开发Linux | 从业余项目正式变为全职工作 | OSDL/Linux Foundation history |
| **2005.04** | 🔄 **Git诞生**：BitMover撤销Linux的免费BitKeeper许可后，Torvalds在**10天内**写出Git的初始版本 | **思想转折**：愤怒转化为创造力。Git的设计体现了Linus的核心理念：(1)分布式=没有单点故障 (2)性能至上 (3)数据完整性（SHA-1）(4)如果没有好工具，自己造一个。这成为开源史上最有影响力的工具之一 | Linux Journal; Graphite blog; LKML |
| **2005.07** | 将Git维护权交给Junio Hamano | 体现了"创建、验证、然后放手"的管理哲学——与Linux本身的管理形成对比 | Git history |
| **2007** | Linux Foundation成立（OSDL与FSG合并），Torvalds成为Fellow | 制度化保障了Linux开发的长期稳定性 | Linux Foundation |
| **2008-2017** | Linux持续增长：Android基于Linux、云计算兴起、容器技术（Docker/K8s） | Linux从服务器扩展到移动端和云端，验证了内核的可扩展性设计 | Industry history |
| **2012** | 获得千禧技术奖（Millennium Technology Prize） | 学术界对开源贡献的正式认可 | Millennium Prize Foundation |
| **2018.09.16** | 🔄🔄 **最重大的个人转折**：在LKML发表公开道歉信，承认自己的攻击性沟通方式伤害了他人，宣布暂时离开内核开发进行自我反思。同时Linux内核采用新的Code of Conduct（基于Contributor Covenant）替代原来的"Code of Conflict" | **思想转折（双重）**：(1) **个人层面**：首次公开承认错误，承认技术卓越不能为人际伤害开脱。(2) **治理层面**：从"Code of Conflict"（基本上说"互相对骂OK"）转向正式行为准则。这对整个开源社区的文化产生了深远影响。Torvalds说："I need to change some of my behavior, and I want to apologize to the people that my personal behavior hurt and possibly drove away from kernel development entirely." | LKML 2018/9/16/167; NYT; Ars Technica |
| **2018.10** | 暂离期间，Greg Kroah-Hartman代理内核维护 | 证明了Linux社区的韧性——项目不会因一人缺席而停摆 | LKML; media |
| **2018.10底** | 回归内核开发（约6周后） | 回归后言辞明显收敛，减少了人身攻击，但技术批评依然犀利 | LKML |
| **2019-2020** | 回归后的"新Linus"——技术直言依旧但减少人身攻击 | 证明了可以保持技术标准而不诉诸羞辱。"I can still say code is shit without calling the person shit" | LKML observations |
| **2021** | Rust for Linux项目开始（Miguel Ojeda主导），初始patches提交 | Torvalds持开放但观望态度，允许实验性代码进入 | LKML; Rust for Linux project |
| **2022.12** | Linux 6.1发布——首次包含Rust基础设施代码（标记为"experimental"） | 里程碑：C语言30年垄断首次被打破，但限制在实验性标记内 | kernel.org |
| **2024早期** | Rust in kernel引发"宗教战争"式辩论：保守C维护者（如Christoph Hellwig）vs Rust倡导者 | Torvalds保持中立仲裁者角色，不站队但维护流程。当Asahi Linux的Hector Martin公开攻击反对者时，Torvalds训斥他："How about you accept that maybe the problem is you?" | Open Source Summit Europe 2024; Ars Technica |
| **2024中期** | 采取"wait and see"到条件性支持的立场，允许Rust贡献但要求尊重现有C接口 | 实用主义再次体现：不是"Rust好/C好"的二元选择，而是"证明它有用就可以进来" | The New Stack; LKML |
| **2024-2025** | 🔄 对AI/LLM的公开态度形成：称AI为"supercharged autocorrect"，是工具而非革命性替代 | **务实定位**：(1)AI是进化不是革命，类似从汇编到C到Rust的演进 (2)人类必须为AI生成代码负责 (3)"Let's wait 10 years and see where it actually goes" (4)引入`Assisted-by`标签要求透明度 | ZDNet; 36kr; Open Source Summit 2025 |
| **2025.09** | Linux 6.17发布——拒绝RISC-V代码提交，称其为"garbage" | 证明2018年后的"新Linus"仍然对代码质量毫不妥协，只是不再攻击人格 | Phoronix; LKML |
| **2025.12** | 🔄 **Linux内核维护者峰会**：Torvalds正式支持移除Rust的"experimental"标签，宣布Rust为"内核核心部分"，"zero pushback" | **思想转折**：从2021年的谨慎观望到完全接纳，历时4年。体现了Torvalds一贯模式——让代码证明自己，而非预判 | The New Stack; Open Source Summit Korea 2025; FreeBuf |
| **2025.12** | Linux 6.18发布（2025年最后一个版本），可能成为LTS版本 | 内核的稳定性和成熟度持续提升 | Open Source Software News |
| **2026.01** | 🔄 **Linux内核接班人计划（Continuity Document）**正式发布：若Torvalds无法履职，72小时内启动白烟机制，TAB+维护者峰会选出继任者 | **思想转折（治理成熟）**：从"Linux is me"到制度化确保项目存续。Torvalds说"no shortage of capable people"——承认项目已超越个人。与2018年事件一脉相承 | IT之家; Phoronix; LKML |
| **2026.02** | Linux 6.19发布；Torvalds宣布下一版本跳过6.20直接到**7.0**，原因："I'm being confused by large numbers (almost running out of fingers and toes)" | 版本号的幽默处理——一贯的反庄严风格 | Help Net Security; 腾讯新闻 |
| **2026.04** | 🔄 **Linux 7.0发布**——里程碑版本：(1) Rust正式从experimental毕业为核心语言 (2) AI辅助开发成为"new normal" (3) 后量子密码学（ML-DSA） (4) XFS自愈文件系统 | **多重意义**：版本号象征新纪元；Rust转正标志技术多元化；AI集成体现务实拥抱新工具；后量子密码体现前瞻性 | 多家中文科技媒体; kernel.org |
| **2026.04** | Torvalds关于AI的最新表态："AI keeps finding corner cases for us—this may be the 'new normal'" | 从"let's wait and see"到承认实际价值——但仍框定为工具角色 | Linux 7.0 release notes coverage |

## 思想转折点总结

### 六大核心转折

1. **1992 - 实用主义确立**（Tanenbaum辩论）
   - 从"学术正确"到"能工作就是好设计"
   - 影响持续至今的所有技术决策

2. **1992 - GPL选择**
   - 接受开源协作模式，但拒绝意识形态极端
   - 塑造了整个Linux生态的商业+自由并存模式

3. **2005 - Git诞生**（被迫创新）
   - "依赖他人的工具是脆弱的"→自己掌控命运
   - 证明了约束催生创新的模式

4. **2018 - 个人行为反思**（最大的人格转折）
   - 从"技术天才不需要情商"到"影响力伴随责任"
   - 证明了56岁的人（当时49岁）仍能改变核心行为模式

5. **2025 - Rust接纳**（技术开放性）
   - 从"C is the only language"到"prove it works and it's welcome"
   - 体现了4年耐心观察后才做判断的决策模式

6. **2026 - 接班人计划**（超越个人）
   - 从"I am Linux"到"Linux will outlive me"
   - 制度化治理的最终成熟

### 贯穿一生的核心思维模式

| 模式 | 表现 |
|------|------|
| **极致实用主义** | BitKeeper选择、GPLv2而非v3、Rust接纳条件 |
| **代码说话** | "Talk is cheap, show me the code"——贯穿所有技术争论 |
| **被迫创新** | Commodore→自己写工具、MINIX限制→Linux、BitKeeper失去→Git |
| **耐心验证后决策** | Rust花了4年从experimental到core；AI"let's wait 10 years" |
| **技术完美主义+人格演变** | 始终拒绝"garbage"代码，但2018后改变了表达方式 |
| **反权威/反庄严** | 命名（Git="混蛋"）、版本号跳转理由、自嘲幽默 |

---

## 来源汇总

- LKML (Linux Kernel Mailing List) archives
- Wikipedia (English/German editions)
- comp.os.minix Usenet archives (1991-1992)
- The New Stack (2024-2025 Rust coverage)
- Ars Technica (2025 Rust in kernel coverage)
- ZDNet (AI in Linux coverage, BitKeeper history)
- Open Source Summit 2024/2025 transcripts
- Linux Journal (Git origin story)
- Graphite.dev (BitKeeper-Git history)
- kernel.org release notes
- IT之家, 36kr, 腾讯新闻 (中文科技媒体, 2026 coverage)
- Help Net Security (kernel 6.19 release)
- FreeBuf (Rust in kernel 2025)
- The New York Times (2018 CoC coverage)
- Phoronix (succession plan, kernel releases)
- Linux Foundation official communications
