# 提交计划

这个仓库已经 `git init` 并暂存了全部文件，但**没有提交**——因为提交作者应该是你自己，我不替你编造身份。

## 发布前先做两件事

```
cd D:\self-employment\commitment-contract-spec
git config user.name "你的名字"
git config user.email "你的邮箱"
```

然后把 `LICENSE` 里的占位行替换掉：

```
Copyright (c) 2026 项目发起人（发布前请将此行替换为你的姓名或组织名）
```

## 建议的三个提交

一条提交做一件事。这样别人翻历史时能看懂这份协议是怎么长出来的。

**提交 1**

```
docs(spec): 增加承诺契约判定协议 v0.1

判定层规范：可判定性分级、判定三态、证据要求、金额阶梯、
申诉复核、状态机与六条不变式。不含资金层定义。
```

包含：`SPEC.md`、`docs/evidence.md`

**提交 2**

```
feat(demo): 单文件可运行演示

浏览器直接打开即可走完 创建→提交→判定→冻结→申诉→结算 全链路。
默认本地规则模式无需 API Key；支持任意 OpenAI 兼容端点做语义条款判定。
模拟记账，不涉及真实资金。
```

包含：`demo/index.html`

**提交 3**

```
docs: 补充复核工作流、贡献指南与待办清单
```

包含：`README.md`、`CONTRIBUTING.md`、`docs/appeal-review.md`、`issues.md`、`.gitignore`、`LICENSE`

## 发布到 GitHub

1. 在 GitHub 新建仓库，**不要初始化 README/.gitignore/LICENSE**（本地已有）
2. 仓库描述建议：
   ```
   A protocol spec for the judgment layer of deposit-based self-discipline apps
   ```
3. Topics 建议（这几个词是别人真正会搜的）：
   ```
   commitment-contract, accountability, habit, llm, verification, protocol, spec
   ```
4. 推送（文件已暂存，按上面的三条提交信息依次 `git commit`）：
   ```
   git commit -m "docs(spec): 增加承诺契约判定协议 v0.1"
   git commit -m "feat(demo): 单文件可运行演示"
   git commit -m "docs: 补充复核工作流、贡献指南与待办清单"
   git branch -M main
   git remote add origin https://github.com/<你的账号>/commitment-contract-spec.git
   git push -u origin main
   ```
5. 打开 `issues.md`，把里面 7 条逐条建成 GitHub Issue，标上 `good first issue` 与 `help wanted`。**这一步比仓库本身更重要**——没有 issue 列表的仓库，等于没有入口。

## 发布后第一周该做什么

仓库本身不会带来人。有动作才会：

- 在 README 顶部放一句能被搜索到的话：*"Why deposit apps get charged-despite-completed wrong, and how to fix the judgment layer."*
- 去 `CUinspace233/stakeword`、`KushagraBharti/Pact` 这两个最接近的仓库开 issue，指出它们缺少证据要求与申诉流程，并链回本协议。这是最精准的曝光渠道。
- 不要把链接发到"求 star"的群。这个仓库的价值在协议本身，不在星数。
