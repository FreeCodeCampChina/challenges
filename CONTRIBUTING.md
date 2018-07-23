# 关于 git 和 github
## 常用词汇
- repo：代码仓库
- PR：即 pull request，合并请求
- branch：分支
- commit：提交记录
- merge：指 PR 合并到代码仓库的操作
- conflicts：合并冲突

## 开始之前
1. 首先，fork 一下 [challenges](https://github.com/FreeCodeCampChina/challenges/pulls) repo
2. 把**你的 fork** 克隆到本地。注意，`your_name` 是你的 github ID：
```bash
git clone https://github.com/your_name/challenges.git
```
3. 切换到 challenges 文件夹：
```bash
cd challenges
```
4. 根据你在翻译的项目名称或者你正在做的事情，新建分支。注意，`your_branch_name` 是你的分支名，如 `translate-basic-html-and-html5`：
```bash
git checkout -b your_branch_name
```
5. 在本地进行代码或文件修改
6. 修改完成后，先添加要提交的文件：
```bash
git add .        # 添加全部有改动的文件

# 或者你也可以添加某一个文件
git add my.json  # 添加 my.json 文件
```
7. 创建 commit。注意，请根据实际情况填写 commit message：
```bash
git commit -m "My commit message"

# 或者你也可以打开你喜欢的编辑器（需要配置），在里面编写 commit message
git commit
```
8. 把本地更新推送到远程（即你的 fork）：
```bash
git push origin your_branch_name
```
9. 打开 github 页面，创建 PR

## 同步远程更新至本地
1. 关联上游 repo 至本地项目。注意，`upstream` 只是一个本地的 reference，你可以根据自己的习惯命名：
```bash
git remote add upstream https://github.com/FreeCodeCampChina/challenges.git
```
2. 获取上游更新，并应用到本地。以下提供三种方式：
    1. 使用 pull 命令：
    ```bash
    git pull upstream translate
    ```
    2. 使用 rebase 命令：
    ```bash
    git fetch upstream
    git rebase upstream/translate
    ```
    3. 使用 pull 命令与 rebase flag（推荐）：
    ```bash
    git pull --rebase upstream translate
    ```

## 注意
1. `pull` 或 `rebase` 之后，如果有 conflicts，可以先使用 `git status` 查看存在 conflicts 的文件。修改成需要的版本后：
    - 如果你使用了 `pull` 命令，你需要 `git add .` 然后 `git commit`
    - 如果你使用了 `rebase` 或 `pull --rebase` 命令，你需要 `git add .` 然后 `git rebase --continue`
2. 解决冲突之后，需要更新至远程，否则只有你的本地有更新：
```bash
git push origin your_branch_name
```
3. 如果出现错误提示（多出现于 `rebase` 和 `pull` 命令），请先使用 `git status` 命令检查本地是否有未解决完成的 conflicts
4. 如果你已经用当前的 branch 开了 PR，那么更新这个 branch 至远程的同时，你的 PR 也会自动更新

## 一些原则
1. 建议使用 [git workflow](https://guides.github.com/introduction/flow/) 来进行分支的管理。这样我们可以提交 PR 之后继续在新的 branch 上进行后续的翻译。若需要更新当前的 PR，任何时候我们都可以切换回来
2. 不建议同时开两个相同类型（比如翻译）的 PR，请等待之前的 merge 之后再开新的 PR
3. 更新（创建）PR 时，请更新 labels，方便管理

## 标签（labels）
1. `ready for review`：新开 PR 的默认状态，请手动添加此标签
2. `need update`：已经 review 过的 PR，需要 PR 提交者按照评论做出修改
3. `comments addressed`：用来表示已经按照评论更新了的 PR，等待下一次 review

