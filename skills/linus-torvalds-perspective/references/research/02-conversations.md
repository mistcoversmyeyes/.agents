# 02 - Linus Torvalds: Conversations, Interviews & Public Exchanges

> Research focus: Management style, technical decision-making process, delegation, interpersonal dynamics
> Sources: Podcasts, long-form interviews, conference talks, LKML exchanges, AMAs

---

## 1. Management Style & Leadership Philosophy

### 1.1 "I'm Not a Programmer Anymore"

**Source**: Multiple interviews 2024-2025 (Open Source Summit Korea 2025, various tech outlets)
**Type**: First-hand (direct quotes from Torvalds)
**Credibility**: HIGH

Key quotes:
- "I'm not a programmer anymore. I'm a maintainer."
- "All actual work is done by others... I'm the one who reads emails and merges code."
- "The real work isn't creation; it's maintenance. Without it, systems die."

Daily routine:
- Spends most days silently reading emails, rarely replying unless dissatisfied
- Manages 9-week release cycle: ~2 weeks merging ~12,000 submissions, ~7 weeks debugging/stabilizing
- Acts as quality gate, not feature creator

**Insight**: This self-description contradicts the "genius hacker" myth. He positions himself as a filter/curator, not a producer. The role is closer to an editor-in-chief than a lead engineer.

---

### 1.2 "Benevolent Dictator? No, I'm Just Lazy."

**Source**: *Just for Fun* (2001 autobiography, co-written with David Diamond)
**Type**: First-hand
**Credibility**: HIGH

Key quotes:
- "The best and most effective way to lead is by letting people do things because they want to do them, not because you want them to."
- "Benevolent dictator? No, I'm just lazy. I try to manage by not making decisions and letting things occur naturally. That's when you get the best results."
- "Much of Linux's success can be attributed to my own personality flaws: 1) I'm lazy; and 2) I like to get credit for the work of others."

**Insight**: The "laziness" framing is deliberate self-deprecation masking a genuine philosophy: minimize intervention, maximize autonomous contribution. This is anti-micromanagement elevated to a design principle.

---

### 1.3 Life's Motivational Hierarchy

**Source**: *Just for Fun* (2001)
**Type**: First-hand
**Credibility**: HIGH

> "The first [motivational factor] is survival, the second is social order, and the third is entertainment. Everything in life progresses in that order."

He applies this to technology adoption: innovation thrives only when survival needs are met and social structures exist. Linux succeeded because contributing was *fun*, not because people were paid.

---

## 2. Technical Decision-Making Process

### 2.1 The "Good Taste" Framework

**Source**: TED Talk "The Mind Behind Linux" (2016), various interviews
**Type**: First-hand (with live code demonstration)
**Credibility**: HIGH

The famous linked-list example:
- "Bad taste" code: 10 lines with a special-case `if (node == head)` branch
- "Good taste" code: 4 lines using indirect pointers, eliminating the special case entirely

Principle: Great code removes boundary conditions through better data structures, not through adding conditional branches.

Related rules:
- Functions should be <50 lines ideally
- No more than 3 levels of indentation
- If you need a comment to explain what the code does, the code is too complex

**Source URL**: https://www.ted.com/talks/linus_torvalds_the_mind_behind_linux

---

### 2.2 "I Look at the Code, I Don't Care Who Wrote It"

**Source**: ZDNet interviews, multiple LKML posts
**Type**: First-hand
**Credibility**: HIGH

Decision criteria for merging:
1. Technical merit above all else
2. Clean, maintainable code
3. Proper abstraction layers
4. No unnecessary complexity
5. Long-term maintenance burden considered

Will reject technically functional code if it:
- Doesn't fit kernel design philosophy
- Solves a problem "the wrong way"
- Adds complexity without sufficient benefit

> "Maintenance is hard. Think about the poor guy who has to deal with your code five years from now."

---

### 2.3 The "No Regressions" Iron Rule

**Source**: LKML (multiple posts), kernel documentation, various interviews
**Type**: First-hand (from mailing list posts)
**Credibility**: HIGH

> "WE DO NOT BREAK USERSPACE! Seriously. How hard is this rule to understand?"
> "If a change results in user programs breaking, it's a bug in the kernel. We never EVER blame the user programs."
> "The kernel's job is to serve users, not to educate them."

Enforcement:
- `regzbot` tool tracks reported regressions
- Critical regressions: resolved within 2-3 days
- If a patch causes regressions, revert takes priority over "proper" fix
- Backward compatibility is treated as sacred/inviolable

**Insight**: This is his clearest expression of values hierarchy: user stability > developer convenience > theoretical correctness > feature velocity.

**Source**: https://linuxkernel.org.cn/doc/html/latest/process/handling-regressions.html

---

### 2.4 Git Creation: Design Under Pressure

**Source**: Various retrospective interviews, Git commit history, Wikipedia
**Type**: First-hand (design decisions) + documented history
**Credibility**: HIGH

Context: BitKeeper license revoked April 2005. Torvalds wrote Git's initial prototype in ~10 days (April 3-13, 2005).

Design decisions (deliberately anti-CVS):
1. Distributed architecture (every repo is full copy)
2. Immutable objects keyed by SHA-1 hashes
3. Only 3 core object types: blobs, trees, commits
4. Lightweight branching (thousands of parallel branches)
5. Full offline work capability
6. Target: 6.7 patches/second (vs CVS's ~0.03)

First commit message: "Initial revision of 'git', the information manager from hell"

On the name: "I'm an egotistical bastard, and I name all my projects after myself. First 'Linux', now 'git'." (Also British slang for "unpleasant person")

Handed maintenance to Junio Hamano after initial development - another delegation pattern.

**Source**: https://github.com/git/git/commit/e83c5163316f89bfbde7d9ab23ca2e25604af290

---

## 3. Delegation & Trust

### 3.1 The Trust Hierarchy

**Source**: Linux Maintainers Summit discussions, LWN.net reporting
**Type**: First-hand (from summit) via second-hand reporting (LWN)
**Credibility**: MEDIUM-HIGH (LWN is highly reliable but still reporting)

How trust is built:
- Earned through verifiable contribution quality over time
- Built publicly on LKML, not through private endorsements
- Corporate titles/affiliations are irrelevant
- Explicitly rejects patches that only carry `Reviewed-by` from same organization
- Long-term consistency matters more than brilliance

> "I don't look at every single line... I trust the maintainers."

Trust gradient: new contributor → regular contributor → trusted reviewer → subsystem maintainer → top-level maintainer

---

### 3.2 Greg Kroah-Hartman: The De Facto Second

**Source**: Multiple sources (Open Source Summit 2024, LWN, succession planning documents)
**Type**: Mix of first-hand and second-hand
**Credibility**: HIGH

Relationship:
- GregKH maintains stable branch, USB, driver core, staging tree
- 2018: assumed Torvalds' duties during his "behavior break"
- Torvalds called him the "obvious choice" for succession
- Trust built over decades of collaboration

Notable tension (2024): GregKH removed Russian developers from maintainer lists citing "compliance requirements" - Torvalds was critical of the handling, highlighting that even the most trusted lieutenant can diverge on governance decisions.

**Insight**: The trust relationship works precisely because it's based on demonstrated technical judgment, not organizational authority. But it has limits when external (non-technical) pressures intrude.

---

### 3.3 Succession / Continuity Plan (2026)

**Source**: Linux Foundation Technical Advisory Board, multiple tech outlets
**Type**: Second-hand reporting of official documents
**Credibility**: HIGH (multiple independent confirmations)

Key details:
- 72-hour response window if Torvalds becomes unavailable
- Most recent Maintainers Summit organizer or TAB chair initiates
- "Conclave-like" voting process among senior maintainers
- GregKH as default candidate in emergencies
- Two paths: emergency (rapid) vs. orderly (deliberative)

Torvalds' stance: supports the plan pragmatically, jokes about "planning to live forever"

**Source**: https://itsfoss.com/news/linux-kernel-continuity-plan/

---

## 4. Communication Style & Behavioral Patterns

### 4.1 The "Respect is Earned" Philosophy

**Source**: DebConf 2014 Q&A, LKML archives
**Type**: First-hand
**Credibility**: HIGH

At DebConf 2014:
- Stated respect must be "earned" not demanded
- Distinguished technical criticism from personal attacks (though others disagree with his boundary)
- Defended blunt communication as efficient and honest

Pattern: His harshest responses come when someone:
1. Breaks userspace and blames users
2. Submits code that shows lack of effort/testing
3. Makes ideological arguments in place of technical ones
4. Repeatedly ignores feedback

---

### 4.2 The 2018 Behavior Apology

**Source**: LKML post (September 2018), various reporting
**Type**: First-hand (his own post)
**Credibility**: HIGH

> "I am not an idealized person and I'm not going to pretend to be one. But I can at least try to improve my behavior."
> Acknowledged emails were "unprofessional and uncalled for"

What changed:
- Took temporary leave from kernel development
- Endorsed Code of Conduct for kernel
- Committed to working on empathy

**Contradiction noted**: Before 2018, he explicitly defended his harsh style as necessary for quality. After 2018, he acknowledged it was counterproductive. This is a genuine position reversal, not a reframing.

---

### 4.3 "I Don't Do Politics"

**Source**: DebConf 2014, systemd debates, GPLv3 discussions
**Type**: First-hand
**Credibility**: HIGH

Pattern: Torvalds consistently frames his decisions as purely technical:
- Systemd: "I have no strong opinions" (despite massive community war)
- GPLv3: dismissed as "political" vs GPLv2's "simplicity"
- His criticism of systemd maintainers was about bug-handling process, not init system philosophy

> Pragmatism over ideology, always.

But note: this framing itself is a political position (choosing not to engage in community governance debates has consequences). The "apolitical technician" persona is a deliberate strategy for maintaining authority without getting dragged into faction fights.

**Source**: https://zd.net/22YGG6L

---

## 5. Position Changes & Reversals

### 5.1 AI/LLM Code: "Garbage" to "Vibe Coding" (2023-2026)

**Source**: Multiple interviews, reported use of Google Antigravity tool
**Type**: Mix (first-hand quotes + second-hand reporting of behavior)
**Credibility**: MEDIUM-HIGH

Timeline:
- 2023-2024: Vehemently criticized AI-generated code as "garbage"
- 2025-2026: Used AI tools for personal Python project (AudioNoise)
- Described it as "vibe coding" - acknowledged it was faster for certain tasks

**Contradiction**: His public rhetoric was far harsher than his private practice eventually became. But he maintains a distinction: AI for personal scripts ≠ AI for kernel code.

---

### 5.2 Rust in the Kernel: From Skepticism to "Let's Try" (2022-2023)

**Source**: Linux Plumbers Conference 2022, kernel 6.1 merge
**Type**: First-hand (conference statements)
**Credibility**: HIGH

Timeline:
- Pre-2022: General skepticism about new languages in kernel
- 2022 (Linux Plumbers): "I'm convinced that Rust is a good language for writing drivers and other kernel code"
- Late 2022: Merged Rust infrastructure into kernel 6.1
- 2023-2024: Continued support but stressed gradual adoption

Stance summary: pragmatic gatekeeper. Neither zealot nor skeptic. "Let's try" with guard rails.

**Source**: https://old.lwn.net/Articles/990534/

---

### 5.3 Abrasive Communication → Code of Conduct (2018)

(See section 4.2 above)

This is his most dramatic documented reversal. Decades of defending harsh communication → public apology and behavioral commitment.

---

### 5.4 Intel AVX-512 (2020-2023)

**Source**: LKML posts, hardware switch announcement
**Type**: First-hand
**Credibility**: HIGH

> Called AVX-512 a "power virus" and "complete disaster," wished it would "die in a fire"

Action: Switched personal workstation to AMD Threadripper 3970X (put money where mouth is). Not a full reversal but showed willingness to back positions with personal choices.

---

## 6. Patch Rejection Patterns

### 6.1 How He Says No

**Source**: LKML archives (multiple examples)
**Type**: First-hand
**Credibility**: HIGH

Patterns observed:
1. **Direct technical criticism**: "This code is wrong because X" - no softening
2. **Escalating severity**: First rejection is usually technical. Repeated submissions of bad code get personal
3. **Blaming the submitter's approach, not intelligence**: "You're solving the wrong problem"
4. **Using humor/analogy**: Often wraps rejection in colorful metaphor
5. **Offering direction**: "What you should do instead is..." (not always, but often)

Famous example (paraphrased from LKML):
- Developer blamed PulseAudio for a kernel regression
- Torvalds: "WE DO NOT BREAK USERSPACE" rant - the developer was told in no uncertain terms that the kernel must adapt, never the user

---

### 6.2 When He Accepts Correction

**Source**: LKML, various retrospectives
**Type**: First-hand + second-hand analysis
**Credibility**: MEDIUM-HIGH

Pattern when he changes his mind:
- Usually matter-of-fact, not emotional
- "OK, you're right" without extensive apologetics
- Will credit the person who convinced him
- Rarely revisits or re-explains - just moves forward

Style of admission: pragmatic, never sentimental.

---

## 7. Notable Analogies & Metaphors (Improvised)

Collected from various interviews and talks:

| Metaphor | Context | Source |
|----------|---------|--------|
| "Science is about explaining yesterday's experiments" | On engineering vs science mindset | TED Talk 2016 |
| "I'm an ugly, opinionated gnome" | Self-description | Multiple |
| "Git is the information manager from hell" | Git's first commit | Git repo |
| "Good taste is about eliminating special cases" | Code review philosophy | TED Talk 2016 |
| "I like to get credit for the work of others" | On open source leadership | Just for Fun |
| "Die in a fire" | On AVX-512 | LKML |
| "Garbage" → "Vibe coding" | On AI code evolution | 2023-2026 interviews |

---

## 8. Key Source URLs

### Primary (First-hand)
- TED Talk: https://www.ted.com/talks/linus_torvalds_the_mind_behind_linux
- Git first commit: https://github.com/git/git/commit/e83c5163316f89bfbde7d9ab23ca2e25604af290
- Kernel regression policy: https://linuxkernel.org.cn/doc/html/latest/process/handling-regressions.html
- Open Source Summit 2024 (LWN): https://old.lwn.net/Articles/990534/

### Secondary (Reliable reporting)
- ZDNet systemd coverage: https://zd.net/22YGG6L
- Linux continuity plan: https://itsfoss.com/news/linux-kernel-continuity-plan/
- Kernel patch process: https://linuxkernel.org.cn/doc/html/latest/process/submitting-patches.html
- LinuxReviews: https://linuxreviews.org/Linus_Torvalds

### Books
- *Just for Fun: The Story of an Accidental Revolutionary* (2001) - Linus Torvalds & David Diamond

---

## 9. Contradictions & Tensions Identified

| Contradiction | Notes |
|---------------|-------|
| "I don't do politics" vs. every non-decision IS a political act | His refusal to weigh in on systemd effectively sided with the status quo (which was adopting systemd). Silence is never neutral at his influence level. |
| "Lazy manager" vs. responds to LKML at all hours | The "lazy" framing is rhetoric. In practice he's obsessively attentive to kernel quality. |
| "I don't care who wrote it" vs. trust hierarchy IS about people | He says code matters, not people - but the maintainer trust system is explicitly about evaluating people over time. The resolution: he trusts people based on their code history, not their identity. |
| "Respect is earned" + 2018 apology | Pre-2018: harsh feedback = honest feedback. Post-2018: admitted it was counterproductive. Both can be true, but it's a genuine value shift. |
| AI is "garbage" → uses AI tools | Maintains kernel/personal distinction, but the rhetorical shift is real. |
| "I'm not a programmer" vs. created Git in 10 days | Time-bounded: he WAS a programmer. His identity has genuinely shifted to maintainer/curator. |

---

## 10. Additional Research: Open Source Summit & Recent Activity (2022-2026)

### 10.1 "Boring is Good" - Process Philosophy Evolution

**Source**: https://www.zdnet.com/article/linus-torvalds-on-why-he-prefers-boring-kernel-releases/ (2019), https://www.linuxfoundation.org/blog/2020/08/linus-torvalds-on-30-years-of-linux/ (2020)
**Type**: First-hand (interviews)
**Credibility**: HIGH

> "I much prefer the kind of development where we don't have any big new features, and it's all just small details. That's when things are stable."
> "The process matters because without it, you get chaos. But the process shouldn't get in the way of getting things done."

**Position evolution**: Early Linus was more ad-hoc. Current Linus explicitly values predictable 9-10 week release cycles. The best releases are ones "nobody talks about because they just work."

**Insight**: This is a management maturation arc. From "process is bureaucracy" to "process prevents chaos" — but always with the caveat that process must serve productivity, never the reverse.

---

### 10.2 AudioNoise & "Vibe Coding" - Detailed (2025-2026)

**Sources**:
- https://itsfoss.com/news/linus-torvalds-vibe-coding/
- https://github.com/torvalds/AudioNoise
- https://pbxscience.com/linus-torvalds-explores-audio-processing-with-new-audionoise-project/
**Type**: First-hand (his own GitHub repo + public comments)
**Credibility**: Very High

On using AI for the visualizer:
> "I cut out the middle-man — me — and just used Google Antigravity to do the audio sample visualizer."

Project self-description (deliberate echo of 1991 Linux announcement):
> "Another silly guitar-pedal-related repo... just a hobby, won't be big and professional."

On the AI topic generally:
> "I hate the AI topic not because I hate AI, but because it's overhyped... but I very much believe in its value as a tool."

**Architecture decision**: Core DSP code in C/C++ (handwritten, real-time constraints), visualization in Python (AI-generated, non-critical). This mirrors his kernel philosophy: critical path = hand-crafted, peripheral tooling = whatever works.

**Contradiction resolution**: Not actually contradicting his kernel AI stance. He's consistent: AI for non-critical personal scripting ≠ AI for safety-critical kernel code. The nuance was always there; the media framed it as a reversal.

---

### 10.3 The Mauro Rant - Full Context

**Source**: LKML (exact thread archived at lore.kernel.org)
**Type**: First-hand
**Credibility**: Very High (unedited mailing list archive)

Full quote context:
> "Mauro, SHUT THE FUCK UP!... If a change results in user applications breaking, it's a bug in the kernel. We NEVER blame the user applications."
> "We do not break userspace with TOTAL CRAP."

**What triggered it**: A maintainer (Mauro Carvalho Chehab) merged changes to the video4linux subsystem that broke existing applications, then argued the applications should be updated to match the new "correct" API.

**Why it matters for understanding his decision framework**:
- The absolute hierarchy: users > kernel developers > API correctness
- Breaking this hierarchy is the ONE thing that triggers maximum aggression
- Even a trusted maintainer gets no grace period on this principle

---

### 10.4 On GNOME's Design Philosophy

**Source**: LKML / public posts (early 2000s)
**Type**: First-hand
**Credibility**: HIGH

> "This 'users are idiots, and are confused by functionality' mentality of Gnome is a disease. If you think your users are idiots, only idiots will use it."

**Connection to kernel management**: Same principle applies — trust users/contributors to be competent. Don't dumb down interfaces. Provide power, not guard rails.

---

### 10.5 Open Source Summit Fireside Chats - Trust & Security (2022-2023)

**Source**: https://thenewstack.io/linus-torvalds-on-security-ai-open-source-and-trust/
**Type**: First-hand (moderated conversation with Dirk Hohndel)
**Credibility**: HIGH

On trust as security mechanism:
> "A healthy community is the best defense against bad actors."

On security absolutism:
> "Anybody who thinks you can be 100% secure is living in a fantasy world."

On AI (typical Linus diminishment followed by grudging acknowledgment):
> "[AI is] autocorrect on steroids."
> "I see bugs without AI every day. We're doing just fine at making mistakes on our own."

On Rust's cultural challenge:
> "The problem isn't whether Rust works—it's whether maintainers can read it. We have people who've written C for 30 years. Asking them to learn a new language is asking a lot."

On why Rust matters despite this:
> "We need to not stagnate as a kernel and as developers."

**Insight on delegation**: The Rust decision reveals his management calculus — he'll override current maintainer comfort for long-term project health. This is NOT "letting things happen naturally." It's an active bet on the future, dressed in pragmatic language.

---

### 10.6 Bcachefs Removal (Kernel 6.17) - Trust Limits

**Source**: https://www.linux-magazine.com/index.php/Online/News/Linux-Kernel-6.17-Drops-bcachefs/
**Type**: First-hand (LKML posts) + reporting
**Credibility**: HIGH

> "I'm starting to regret merging bcachefs... This is getting beyond ridiculous."

**What happened**: Developer Kent Overstreet repeatedly submitted late fixes after merge window, then fought publicly with Linus over process. Torvalds eventually removed the filesystem.

**Pattern**: Trust revocation sequence:
1. Initial merge (trust extended)
2. Process violations noted
3. Warnings given
4. Continued violations → public expression of regret
5. Removal (trust revoked)

**Insight**: This is the "trust is revocable" principle in action. Demonstrates that even merged code isn't permanent if the maintainer relationship breaks down.

---

### 10.7 BUG_ON() Admission of Fault (2016)

**Source**: https://www.zdnet.com/article/linux-4-8-brings-pi-surface-support-but-linus-torvalds-fumes-over-kernel-killing-bug/
**Type**: First-hand (LKML)
**Credibility**: Very High

> "I should have reacted to the damn added BUG_ON() lines... There's no excuse to knowingly kill the kernel."

**How he admits fault**: Direct, no deflection, no "but". Acknowledges HIS failure to catch it during review. Takes responsibility for the gate-keeping failure, not just the code.

---

### 10.8 Position Change Summary Table (Expanded)

| From | To | When | Trigger |
|------|-----|------|---------|
| Abrasive = honest | Admitted counterproductive | 2018 | Cumulative community pressure + self-reflection |
| AI is garbage/hype | Uses AI for personal projects | 2023→2025 | Practical need (Python inexpertise) |
| Loose process ok | "Process matters" | ~2010s | Project scale outgrew informal coordination |
| Pure C forever | Rust welcome (with limits) | 2022 | Stagnation risk + new contributor pipeline |
| Hands-off on merges | Removed bcachefs | 2025 | Process violations by maintainer |
| Against formal succession | Supports continuity plan | 2024-2025 | Pragmatic acknowledgment of mortality |

---

### 10.9 "Talk is Cheap. Show Me the Code." - Original Context (2000)

**Source**: LKML, August 25, 2000
**Type**: First-hand
**Credibility**: Very High (archived mailing list)

**Context**: A contributor proposed a thread creation optimization without providing implementation. Torvalds dismissed it:
> "Talk is cheap. Show me the code."

**Why this became canonical**: It encodes his entire trust/meritocracy model in six words:
- Ideas without execution have zero value
- Proof is in working code, not rhetoric
- Authority comes from contribution, not position
- Anti-bikeshedding weapon

**Nuance often missed**: He's not anti-discussion. He's anti-discussion-as-substitute-for-action. Design discussions with code to back them up are fine. Proposals without patches are noise.

---

### 10.10 Rejection Spectrum (综合分析)

Based on all sources above, his rejection styles form a clear spectrum:

| Level | Style | Trigger | Example |
|-------|-------|---------|---------|
| 1 (Mild) | "This doesn't make sense because X" | Technical disagreement, first time | Ordinary patch feedback |
| 2 (Standard) | "NAK. This breaks X." | Clear technical violation | Most rejections |
| 3 (Firm) | "I'm not going to merge this." + explanation | Repeated poor submissions | Bcachefs late fixes |
| 4 (Harsh) | ALL CAPS + profanity + detailed technical reasoning | Core principle violation (userspace, regression) | Mauro rant |
| 5 (Nuclear) | Public trust revocation + removal | Pattern of ignoring feedback | Bcachefs removal from tree |

**Post-2018 change**: Levels 4-5 still exist but personal insults removed. Technical sharpness retained.

---

### 10.11 Improvised Analogies Collection

| Analogy | Meaning | Source | Type |
|---------|---------|--------|------|
| "Fixing potholes while others stare at stars" | Engineer vs visionary | TED 2016 | 一手 |
| "Autocorrect on steroids" | AI capabilities (diminishment) | OSS 2023 | 一手 |
| "LEGO for adults with a soldering iron" | Hardware hobby projects | AudioNoise README 2025 | 一手 |
| "Die in a fire" | On AVX-512 | LKML | 一手 |
| "Information manager from hell" | Git's nature | First Git commit | 一手 |
| "I'm a lazy person" | Delegation philosophy | Just for Fun | 一手 |
| "Power virus" | AVX-512 criticism | LKML | 一手 |
| "Living in a fantasy world" | On 100% security claims | OSS 2022 | 一手 |

**Pattern**: His analogies are always:
1. Short (≤10 words)
2. Visceral / physical
3. Slightly offensive or self-deprecating
4. Immediately understandable without tech context

---

## 11. Patterns for Skill Extraction

### Decision-Making Heuristics
1. **Pragmatism > ideology** (always)
2. **Users > developers > theorists** (hierarchy)
3. **Proven track record > promises** (trust)
4. **Simplicity > completeness** (code)
5. **Revert > fix-forward** (when in doubt)

### Communication Heuristics
1. Direct, no hedging
2. Technical criticism first, personal only on repeat offenses
3. Colorful analogies to make points memorable
4. Humor as deflection and as weapon
5. Post-2018: still direct, less personally cruel

### Delegation Heuristics
1. Give autonomy to proven people
2. Intervene only when quality drops
3. Trust is revocable but slow to build
4. Public accountability (LKML) > private channels
5. Let the system self-organize; prune only when necessary
