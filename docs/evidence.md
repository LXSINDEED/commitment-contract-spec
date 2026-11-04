# 事实来源与待核实条目

这份协议里的每一条原则都对应一个外部事实。这里列出出处，并**明确区分「已核实」与「仅引述」**——后者不应被当作定论使用。

## 一、现有产品的事实

### stickK

| 事实 | 状态 | 来源 |
|---|---|---|
| 2007 年由三位耶鲁学者创立，免费无订阅 | 已核实 | `https://www.stickk.com/aboutus` |
| 押金去向四选：朋友/对手、公益机构、stickK、反公益机构 | 已核实 | `https://stickk.zendesk.com/hc/en-us/articles/206833157-How-it-Works` |
| 判定靠人（Referee），裁判可推翻用户的成功报告 | 已核实 | 同上 |
| 官方口径：无押金无裁判 29% 达成率，有押金 80% | 已核实（官方自述） | `https://www.library.hbs.edu/working-knowledge/the-business-of-behavioral-economics` |
| Trustpilot 约 2.1/5 | **仅引述，未直接核对** | 两家第三方聚合页均引用，未打开 Trustpilot 原页验证 |
| iOS 约 3.3 星 | 仅引述 | `https://www.accountablo.com/blog/accountability-partner-app` |
| 约 2020 年起无实质功能开发 | 仅引述 | `https://www.accountablo.com/blog/beeminder-vs-stickk` |

### Beeminder

| 事实 | 状态 | 来源 |
|---|---|---|
| 押金归平台，官方原话承认"收罚金就是我们的商业模式" | 已核实 | `https://blog.beeminder.com/newbees/` |
| 押金指数递增 $5 → $10 → $30 → $90 → $270 → $810 → $2,430 → $7,290 | 已核实 | `https://help.beeminder.com/article/49-why-should-i-use-beeminder-over-stickk` 等帮助页 |
| 40+ 自动数据源 | 已核实 | 官网帮助页 |
| Akrasia Horizon：一周内放宽目标不生效 | 已核实 | `https://doc.beeminder.com/jargon` |
| derail 后 24 小时内可取消 | 已核实 | `https://help.beeminder.com/article/17-what-happens-when-i-derail` |
| 定价：免费 3 目标 / Infinibee $8 / Bee Plus $16 / Beemium $81 每月 | 已核实 | `https://bmndr.co/home` |
| 官方 iOS 客户端开源（BeeSwift） | 已核实 | `https://github.com/beeminder/BeeSwift` |

> Beeminder 是最重要的反例。它证明了"押金归平台"能跑通商业模型，也证明了这会给判定带来系统性偏向——用户夸客服能退钱，但误判导致的假 derail 是长期抱怨点。

### Commit（thecommitapp.com）

| 事实 | 状态 | 来源 |
|---|---|---|
| 长期 beta，仅 iPhone + TestFlight | 已核实 | `https://thecommitapp.com/` |
| 押金 $1–$500，事前不扣，miss 后冻结 72 小时 | 已核实 | `https://www.thecommitapp.com/commitment-agreement/` |
| 九种证据要求，含实时拍摄、时间戳、位置 | 已核实 | `https://thecommitapp.com/how-it-works/` |
| Commit AI 打分，不确定时升级人工或指定朋友审 | 已核实 | 同上 |
| 合约明确写"是服务费，不是押金/对赌/捐款，无抵税收据" | 已核实 | `https://www.thecommitapp.com/commitment-agreement/` |
| 10 个 grace token，可 48 小时内撤销 | 已核实 | 同上 |
| 官网计数器显示 0 / $0 / 0 人 | 已核实 | 首页实测 |

> 注意：Commit 的站点文案在 beta 阶段反复变动（private/public beta、$5–$200 与 $1–$500 并存）。引用前必须重新抓取，不要用旧口径。

> 另注意命名撞车：App Store 上叫 "Commit" 的应用至少 5 个（Nathan Barry 的旧 Commit 已于 2026-10-13 下架，另有 GetCommit、ThenCommit、运动押金版 Commit App、Solana 版 Commit）。引用评分时必须锁域名，否则会串。

## 二、学术证据

| 研究 | 结论 | 对本协议的意义 |
|---|---|---|
| Giné, Karlan & Zinman (2010) | 仅 11% 的人愿意接受押金合约；六个月尼古丁检测通过率高出 3 个百分点（不是 3 倍）；12 个月突击复测仍成立 | 押金方案的自愿采纳率极低。产品早期瓶颈不在机制设计，在"让人肯押真钱" |
| Volpp et al. (2008), JAMA | 减重 14.0 vs 3.9 磅；达标率 47.4% vs 10.5% | 押金有效，但效应依赖持续投入 |
| Halpern et al. (2015), NEJM | 奖励组 15.7% vs 存款组 10.2%；但仅 13.7% 愿选存款，愿意选的人里存款组约 52% vs 17% | **最关键的一条**：押金的效果集中在"本来就愿意押钱"的少数人身上 |
| Mantzari et al. (2015), meta | 激励撤除后效果一般维持约 3 个月 | 押金不是长期解药，是启动器 |
| Royer, Stehr & Sydnor (2015) | 健身合约可维持一年 | 长期合约在特定场景可行 |

> 对本协议的直接含义：**不要在设计判定协议时假设用户会为它押钱。** 判定层要足够便宜、足够自动化，因为在真实场景里愿意押钱的人只有一到两成。

## 三、GitHub 开源现状

检索时间 2026-11，GitHub Search API。

| 查询 | 命中 | 有用发现 |
|---|---|---|
| `stickk OR beeminder OR taskratchet OR forfeit` | 589 | 几乎全是 Beeminder 客户端/插件，无押金 App 本体 |
| `"commitment contract"` | 30 | 少量小项目，最高 2 星 |
| `commitment contract OR stake money accountability` | 4 | 极稀疏 |
| `topic:accountability` | 510 | 被机器学习可解释性仓库污染，与本主题无关 |
| `stake AI verify in:description` | 41 | 多为 DePIN / 算力质押，非自律应用 |

**最高星的相关仓库：**

- `beeminder/BeeSwift`（33★，Swift，官方 iOS 客户端，持续更新）
- `tsubery/quantifier`（42★，Ruby，已归档，Beeminder 数据集成）
- `Sodaware/beeminder.el`、`mbork/beeminder.el`（各 28★，Emacs 客户端）

以上全部是**接 API 的壳**，不含押金与判定逻辑。

**概念级项目（0–2★，全部为黑客松产物）：**

- `CUinspace233/stakeword`（2★）— AI 驱动的链上承诺合约，Claude 负责教练、验证、结算。与本协议最接近，但无证据要求、无申诉流程
- `KushagraBharti/Pact`（0★）— Solana 赛道黑客松第一名，押金托管 + 同伴投票判定
- `Lordsans-404/LockD` — 状态机 Active → Frozen → Redeeming → Claimed，漏签冻结后完成赎罪任务赎回 80%、罚没 20%
- `eliaslehner/Motify` — Base 上的押金池，接入 GitHub / WakaTime / Farcaster 自动验证
- `godsflaw/crucible`、`uttrly/UTTR`、`ashbi8137/pay-and-promise`、`suhaqazi/pirates-of-the-compiler` 等

**结论：** 这个品类在开源世界没有任何成熟实现。已有项目几乎全部选择"链上托管"来回避"平台收钱"的信任问题——这从侧面印证了 `SPEC.md` 原则一。而没有项目解决"判不出来怎么办"，那正是本协议的全部内容。

## 四、必须自行核对的三项

以下是本文档中**依赖二手转述**的部分，正式对外引用前请自行打开原始页面核对：

1. stickK 的 Trustpilot 分数（2.1/5）
2. stickK 的 iOS 评分（3.3 星）与合约总量（53.3 万）
3. Habi 横评的具体分数（stickK 3.0/5、Beeminder 4.0/5）

第三方横评本身有商业立场（多为竞品站），引用时标明"第三方评测口径"，不要写成客观事实。
