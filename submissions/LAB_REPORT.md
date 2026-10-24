# 实验报告 / LAB_REPORT

> 做题者填写本文件后，随功能分支一并提交，并在 PR 中带上。

## 基本信息

- **GitHub 用户名：123-tjk
- **功能分支名：git-practice-lab分支
- **PR 链接：https://github.com/kiramint/git-practice-lab/pull/1

## 阶段清单

- [ ] Stage 0 — Fork、clone、upstream、创建 `lab/<username>`
- [ ] Stage 1 — 工作区 / 暂存区 / commit
- [ ] Stage 2 — 分支、merge、冲突解决
- [ ] Stage 3 — 坏提交 + revert
- [ ] Stage 4 — 添加 submodule `third_party/kit`
- [ ] Stage 5 — fetch upstream、push、开 PR

## 简答题

### 1. 工作区、暂存区、已提交（commit）分别是什么？

工作区：可以对文件的内容和代码修改的区域
暂存区：对做出的修改进行保存，用于检查对错
已提交：完成对原文件的修改

### 2. `git pull` 和 `git fetch` 有何不同？你通常何时用哪个？

git fetch:将远端的内容放进暂存区
git pull:将远端的内容同步进工作区

### 3. 什么情况下不应该对已推送的共享分支使用 `git reset --hard`？为什么？

多人协作时不要使用，会连同别人的内容一块删除

### 4. 带 submodule 的仓库 clone 后子目录是空的，常见原因是什么？怎么处理？

.gitmodules 没提交,让仓库维护者补交 .gitmodules 和 gitlink

## 关键 commit（填写短 hash 或完整 hash）

| 说明 | Hash |
|------|------|
| Stage 1 第一次较好的 commit | |
c75ab2d7937fc269c2185b0d87da9758c3095d1c
| Stage 2 冲突解决（或合并）commit | |
b2fa91f76cbf2f847a2f8e2b4fb6d67a62b5b536
| Stage 3 revert 产生的 commit | |
05237311b7ccb71759bed43099efefda86c8c17a
| Stage 4 submodule add 的 commit | |
17c4e36b2e970c8d2b0db57f799b0c5498a79bef

## Stage 2 补充

- 普通 merge 结果：合并提交（merge commit）
- 冲突解决简述：修改相同地方的内容会引起冲突，手动抉择需要的方案即可

## Stage 5 补充

- 同步 `upstream/main` 时使用：merge　
- 选择理由：merge能看懂，rebase感觉怪怪的，怕出问题

## 其他备注（可选）

<!-- 例如：只用了非交互式 add、环境限制、踩过的坑等 -->
