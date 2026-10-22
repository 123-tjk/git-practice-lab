# 作业说明 / ASSIGNMENT

按阶段完成一条**完整流程**。每阶段写明：**目标**、**要求动作**、**交卷要写什么**。命令名保留英文；具体怎么敲由你查文档、试出来——开放到够思考，具体到够评分。

伴侣 submodule 仓库：https://github.com/kiramint/git-practice-kit  
（本仓库**未**预先添加 submodule，Stage 4 由你自己添加。）

---

## Stage 0 — 准备

### 目标
在 GitHub 上拿到自己的副本，本地可推送，并能跟踪上游原仓库。

### 要求动作
1. 在 GitHub 上 **Fork** `kiramint/git-practice-lab`。
2. `git clone` **你自己的 fork**（HTTPS 或 SSH 均可）。
3. 添加名为 `upstream` 的 remote，指向：  
   `https://github.com/kiramint/git-practice-lab.git`  
   用 `git remote -v` 确认同时有 `origin`（你的 fork）和 `upstream`（原仓库）。
4. 从默认分支创建并切换到：`lab/<your-github-username>`。

### 交卷要写什么（LAB_REPORT）
- 你的 GitHub 用户名
- 分支全名 `lab/...`
- `origin` / `upstream` 是否都配置好（简短确认即可）

---

## Stage 1 — 工作区 / 暂存区 / commit

### 目标
分清工作区、暂存区、已提交历史；能在三者之间移动改动并写出清晰 commit。

### 要求动作
1. 编辑 `workspace/notes.txt`（仓库里已有起始内容），至少改几行，可另加你自己的笔记。
2. 用 `status`、`diff`、`diff --staged` 观察：**未暂存** vs **已暂存** 的区别；在 LAB_REPORT 里用自己的话解释三者（工作区 / 暂存区 / commit）。
3. 尽量练习「只暂存部分改动」（例如 `git add -p` 或等价方式）；若环境不支持交互，说明你用了什么替代方案。
4. 做一次信息清晰的 `commit`（写清「改了什么、为什么」）。
5. 再改一次同一文件或相关文件；用 `restore` / `reset`（选合适的）在工作区与暂存区之间搬动改动，并在报告里记录你做了哪几步、结果如何。

### 交卷要写什么
- 工作区 vs 暂存区 vs 已提交：各 1～3 句
- 你第一次「好的」commit 的完整或短 hash
- 你如何在三个区域间移动改动的简要步骤

---

## Stage 2 — 分支与 merge

### 目标
创建功能分支、合并回实验分支，并主动制造、解决一次冲突。

### 要求动作
1. 当前在 `lab/<username>` 上，创建并切换到 `feature/greeting`。
2. 编辑 `workspace/greeting.md`，提交一次（信息写清楚）。
3. 切回 `lab/<username>`，把 `feature/greeting` **merge** 进来。  
   - 若是快进（fast-forward），在报告里说明；  
   - 若产生合并提交，也说明；任选合理策略，但要写清你选了什么、历史大概长什么样。
4. **故意制造冲突**：在两个不同分支上修改 `workspace/greeting.md` 的**同一行**（或同一小段），再 merge，出现冲突后解决、完成合并提交。

### 交卷要写什么
- 普通 merge 是快进还是合并提交
- 冲突解决那次的 commit hash
- 冲突时你改了文件的哪一部分、如何判定「解决完成」

---

## Stage 3 — 历史回溯

### 目标
学会用日志定位问题，并用**适合已分享历史**的方式撤销错误提交。

### 要求动作
1. 故意做一个「坏提交」：新增 `workspace/oops.txt`，内容写一些无意义的文字，并 commit。
2. 用 `log`（必要时 `reflog`）找到这个坏提交。
3. **优先使用 `git revert`** 撤销该坏提交（保留历史、对已推送分支更安全）。  
   在报告中简要说明：什么时候**绝不该**对已推送的共享分支使用 `reset --hard`。
4. （可选）自行了解 `reset` 与 `revert` 的差异，但交卷以 revert 结果为准。

### 交卷要写什么
- 坏提交 hash、revert 产生的新 commit hash
- 「何时不该 `reset --hard`」的简短回答

---

## Stage 4 — Submodule

### 目标
把伴侣仓库加为 submodule，并理解「带 submodule 的仓库该怎么 clone」。

### 要求动作
1. 在仓库根目录添加 submodule（路径必须如下）：

   ```text
   git submodule add https://github.com/kiramint/git-practice-kit.git third_party/kit
   ```

2. 查看 `third_party/kit` 下的 `kit/VERSION`、`kit/TIPS.md`，确认内容可读。
3. **提交**这次 submodule 添加（父仓库会记录 `.gitmodules` 与子模块指针）。
4. 在 LAB_REPORT 中说明：别人以后如何正确 clone **已经包含** submodule 的仓库（`--recurse-submodules` 和/或 `submodule update --init`）。
5. （可选）说明如何更新子模块指针；可不改 kit 内容，写清原理即可。

### 交卷要写什么
- submodule add 那次 commit 的 hash
- 「clone 完子目录是空的」常见原因与解决办法
- （可选）更新指针的步骤概述

---

## Stage 5 — 与上游同步 + push + PR

### 目标
把上游更新合进自己的实验分支，推送，并向原仓库交卷。

### 要求动作
1. `git fetch upstream`，然后将 `upstream/main` 合并或 rebase 进你的 `lab/<username>`。  
   在报告中写明你选了 **merge** 还是 **rebase**，以及为什么。
2. 确保 `submissions/LAB_REPORT.md` 已填完整（含各阶段 hash 与简答题）。
3. `git push -u origin lab/<username>`（推到你的 fork）。
4. 在 GitHub 上向 **`kiramint/git-practice-lab`** 开 Pull Request：
   - **base：** `main`（原仓库）
   - **compare：** 你的 `lab/<username>`
   - **标题：** `[Lab] <username> 完成 Git 实操`
   - 正文可使用仓库自带的 PR 模板；确认 LAB_REPORT 与清单已勾选

### 交卷要写什么
- 同步上游时用的是 merge 还是 rebase，及理由
- PR 链接（开好后填回 LAB_REPORT）

---

## 评分关注点（给你自检）

| 主题 | 期望看到 |
|------|----------|
| clone / remote | fork + origin + upstream |
| 工作区/暂存区/commit | 说得清 + 有实践痕迹 |
| 分支 / merge / 冲突 | 有冲突解决提交 |
| 历史 | 有 revert，而非只靠删文件 |
| submodule | `third_party/kit` 存在且已提交 |
| GitHub | 规范分支名 + 规范 PR 标题 |
| push / pull / fetch | Stage 5 体现 fetch 与同步 |

（可选加分：在报告里提一句「自己在 GitHub 上新建空仓库并首次 push」的步骤——不必真的建第二个作业仓。）

完成后：检查清单、填好报告、开 PR。祝练习顺利。
