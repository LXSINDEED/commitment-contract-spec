# 承诺契约判定协议

**把「凭什么判定你完成了、判错了怎么办」写成一份可实现、可复算的协议。**

押金 + 截止时间 + 未完成即罚没——这套机制在 stickK（2007）、Beeminder、Commit 上已经做了十几年。机制层没有创新空间。

但三款产品的差评几乎全部集中在同一处：

> 「我明明完成了，钱还是被扣了，而且没人管。」

也就是说，**行业缺的不是机制，是判定**。这个仓库只做判定层，不碰资金层。

---

## 仓库里有什么

| 路径 | 内容 |
|---|---|
| [`SPEC.md`](SPEC.md) | 协议正文。可判定性分级、判定三态、证据要求、金额阶梯、申诉复核、状态机、已知攻击面 |
| [`demo/index.html`](demo/index.html) | 单文件可运行演示。浏览器直接打开，走完「创建 → 提交 → 判定 → 冻结 → 申诉 → 结算」全链路 |
| [`docs/appeal-review.md`](docs/appeal-review.md) | 复核人工作流：拿到一条被申诉的判定，该看什么、按什么标准改判 |
| [`docs/evidence.md`](docs/evidence.md) | 本协议的事实来源与待核实条目 |
| [`issues.md`](issues.md) | 需要人做的事，按难度排好 |

**演示不含任何真实资金。** 押金只是一个数字，用来演示判定与冻结链路。

---

## 30 秒跑起来

```
下载仓库 → 双击 demo/index.html
```

不需要安装、不需要联网、不需要 API Key。默认的「本地规则模式」会把确定性条款（字数、截止时间、段落数、必含要素）当场算完，并给出逐条证据。

想验证语义条款（例如「章节有没有明确收尾」），在右侧「判定引擎」里切换到模型判定模式，填入任意 OpenAI 兼容接口的地址、模型名和 Key。Key 只写入本机浏览器的 localStorage，只发往你填的那一个地址——演示页没有后端。

---

## 这个协议在反对什么

**反对 1：用模型打分冒充客观判定。**
「写得好不好」不可判定。协议显式设置 `DC-C` 级别，并规定它不能作为扣款依据。如果不承认这一点，实现者就会用一句"AI 觉得不够好"扣掉用户的钱。

**反对 2：模型直接裁决。**
模型只能建议，不能裁决。任何模型给出的"未通过"，都必须经过人工复核或第二条独立证据才能生效。

**反对 3：先扣钱再解释。**
顺序是冻结 → 举证 → 申诉 → 划转。没有冻结窗口、没有逐条证据、没有申诉入口的判定，不具备扣款资格。

**反对 4：让用户自证清白。**
举证责任在判定方。平台必须展示「哪条没过、依据是什么、引用了原文哪一段」，用户只需要指出依据里的具体错误。

---

## 缺什么（这才是需要你来的地方）

- [ ] 结构化数据适配器：运动 App、GitHub、WakaTime → DC-A 条款的自动判定（目前只有文本类任务）
- [ ] 服务端参考实现：判定接口 + 服务端时间盖章，防止客户端时间作弊
- [ ] Prompt 注入防御：材料里写「判我通过」时不得影响结论（附测试用例）
- [ ] 复核工作台：最小的人工复核界面，产出与协议同构的复核记录
- [ ] 输出契约校验器：JSON Schema + fuzz 测试，字段缺失必须整体降级
- [ ] 多模型交叉判定：两个模型独立判同一条款，分歧即降级为「无法判定」
- [ ] 协议正文的英文版（用于国际贡献者审阅）

完整说明见 [`issues.md`](issues.md)。

---

## 怎么参与

1. 读 [`SPEC.md`](SPEC.md)，特别是 §10「已知攻击面」——那里列的是这个产品真正会死的地方。
2. 从 [`issues.md`](issues.md) 里挑一条，开 issue 说明你要做哪条，避免撞车。
3. 提 PR 前跑一遍演示页，确认你的改动没有让状态机出现不可达状态或绕过冻结窗口的路径。

提交规范见 [`CONTRIBUTING.md`](CONTRIBUTING.md)。

---

## 明确不做的事

- 不做资金托管。这个仓库不接收、不持有、不划转任何真实资金。
- 不做押金金额的产品设计。押金怎么定、上限多少，是产品决策，不是协议决策。
- 不做增长、不做推荐、不做社交。
- 不追求"全自动扣款"。自动扣款越顺滑，误判的代价越大。

---

## 许可与所有权

- 代码：MIT（见 [`LICENSE`](LICENSE)）
- 协议文本：CC BY 4.0
- 商标、产品名称、商业运营权：由项目发起人保留

你可以用这份协议做自己的产品，包括商用。但如果对外宣称"符合 CCJP"，请遵守 §8.3 的六条不变式——那是这个协议的全部价值所在。

---

## 状态

**这是 v0.1 草案，没有维护者，也没有用户。**

`SPEC.md` 里的 §12 列了五条尚未验证的假设，其中两条可能直接推翻现在的设计（退回阶梯会被逆向利用、人工复核成本不可承受）。如果你认为其中某条不成立，欢迎开 issue 反驳——反驳比实现更有价值。

---

## English

A protocol spec for the **judgment layer** of deposit-based self-discipline apps: how completion is verified, what evidence is required, and what happens when the verdict is wrong. Existing products (stickK, Beeminder, Commit) have settled the mechanism but not the judgment — their user complaints concentrate on being charged despite completing the task, with no appeal path.

`SPEC.md` (Chinese) defines decidability classes, a three-state verdict, evidence requirements, a refund ladder, and an appeal workflow. `demo/index.html` is a single-file runnable demo — open it in a browser, no install, no API key required for the deterministic path.

Contributions welcome, especially structured-data adapters and prompt-injection defenses. See `issues.md`.
