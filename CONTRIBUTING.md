# 关于 git 和 github
## 常用词汇
- repo：代码仓库
- PR：即 pull request，合并请求
- branch：分支
- commit：提交记录
- merge：指 PR 合并到代码仓库的操作
- conflicts：（合并）冲突

## 开始之前
1. 首先，fork 一下 [challenges](https://github.com/FreeCodeCampChina/challenges.git) repo
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
# 建议每次都从 translate 分支建立新的分支
# 请参考后面的“常见问题”
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
1. 关联上游 repo 至本地项目：
```bash
git remote add upstream https://github.com/FreeCodeCampChina/challenges.git
```
2. 获取上游更新，并应用到本地：
```bash
git pull --rebase upstream translate
```

## 注意
1. `pull` 或 `rebase` 之后，如果有 conflicts，可以先使用 `git status` 查看存在 conflicts 的文件。修改成需要的版本后，使用 `git add .` 然后 `git rebase --continue`
2. 解决冲突之后，需要更新至远程，否则只有你的本地有更新：
```bash
git push origin your_branch_name
```
3. 如果出现错误提示，请先使用 `git status` 命令检查本地是否有未解决完成的 conflicts
3. 任何时候出现错误，不必惊慌。先使用 `git status` 命令检查当前所在的分支、当前目录是否纯净（clean），以及本地是否有未解决完成的 conflicts
4. 如果上一步没问题，你可以用 `git push -f origin your_branch_name` 来更新远程
5. 如果你已经用当前的 branch 开了 PR，那么更新这个 branch 至远程的同时，你的 PR 也会自动更新

## 常见问题
<details>
    <summary>如何查看我当前处于哪个分支？</summary>
    <code>git branch</code> 可以列出本地所有的分支名，前面打星号（*）的就是你当前所在的分支
</details>
<details>
    <summary>如何切换分支？</summary>
    <code>git checkout some_branch_name</code> 就可以切换到对应的分支。以及，<code>git checkout -</code> 可以切换到上一个切换过的分支。在两个分支之间来回切换的时候，这个命令会很有用
</details>
<details>
    <summary>新建分支的时候，与我当前所在的分支有关联么？</summary>
    有。新建分支的时候，当前所在分支的所有 <code>commit</code> 也会添加到新的分支里面。以及，如果你本地有未 <code>commit</code> 的改动（哪怕已经 <code>add</code> 过），同样会在新建分支的时候带过去。
</details>
<details>
    <summary>既然切换 branch 时代码会跟着走，我正在别的分支上翻译，突然让我去更新之前开了 PR 的另一个分支，我该怎么办？</summary>
    <p>你有两个选择，<code>commit</code> 或者 <code>stash</code>：</p>
    <ol>
        <li><code>commit</code> 很简单，在当前分支上 <code>git add .</code> 然后 <code>git commit -m "xx"</code>，这时候你就可以使用 <code>checkout</code> 命令切换到其他分支了</li>
        <li>在当前分支上 <code>git stash</code>，然后切换到其他分支。完成那边的更新后，切换回来，然后 <code>git stash pop</code>，你之前的代码改动就都回来了</li>
    </ol>
    <p>需要注意的是，使用 <code>git stash pop</code> 会有丢代码的潜在风险，推荐使用 <code>git stash apply stash@{x}</code>，其中 <code>x</code> 为一个数字</p>
    <p>如果你不确定你的做法是否正确，或者不了解这个命令，请在使用之前查清资料，或者在群里提问</p>
    <p><strong>切换分支前，未防止把本地弄乱，前先使用 `git status` 来检查本地是否 “clean”</strong></p>
</details>
<details>
    <summary>我可不可以根据远程的分支（比如 upstream 的 translate 分支）来创建本地分支？</summary>
    可以：
    <pre><code>
    git fetch upstream
    git checkout -b my_branch_name upstream/translate
    </code></pre>
</details>
<details>
    <summary>每次都从远程创建分支太麻烦，我可不可以直接从本地创建分支？</summary>
    可以。建议使用本地的 translate 分支保持与 upstream 中的 translate 分支保持更新。这样做的好处是：
    <ol>
        <li>每次新建分支的时候，切换到本地的 translate 分支，然后 <code>git checkout -b my_new_branch</code> 就好了</li>
        <li>如果 upstream 的 translate branch 有更新，你只需要在切换到 translate 分支之后，<code>git pull --rebase upstream/translate</code> 即可完成对本地 translate 分支的更新。再创建新的分支，就是基于 upstream 里最新的代码了，这样可以减少 conflicts 出现的可能</li>
    </ol>
</details>
<details>
    <summary>我在一个分支上 commit 了我的代码，这时候 upstream 更新了，我该怎么做？</summary>
    <pre><code>
    git pull --rebase upstream/translate
    </code></pre>
</details>
<details>
    <summary>我的本地 translate 分支已经有我的 commit 了，那我该如何用这个分支作为与 upstream translate 同步的分支呢？</summary>
    <p><strong>如果你目前在 translate 提交的内容不再需要了（比如，已经 merge）</strong>，那你可以先切换到 translate，然后：</p>
    <pre><code>
    git fetch upstream
    git reset --hard upstream/translate
    </code></pre>
    <p>虽然 <code>git reset</code> 命令不危险，但在执行这个操作之前，建议你先在群里问一下</p>
</details>
<details>
    <summary>命令好长，我不想记</summary>
    <code>alias</code> 了解一下。在命令行里执行：
    <pre><code>
    git config --global alias.gx 'pull --rebase upstream/translate'
    </code></pre>
    <p>下次，执行 <code>git gx</code>（记忆：git 更新），就会执行你定义好的命令了</p>
</details>

## 一些原则
1. 建议使用 [git workflow](https://guides.github.com/introduction/flow/) 来进行分支的管理。这样我们可以提交 PR 之后继续在新的 branch 上进行后续的翻译。若需要更新当前的 PR，我们随时可以切换回来
2. 不建议同时开两个相同类型（比如翻译）的 PR，请等待之前的 merge 之后再开新的 PR
3. 如果你的 PR 已经被 review 过，请不要再添加新的翻译内容，根据 comment 修改好当前的 PR 即可。后续的翻译你可以等当前翻译 merge 后再开始做，或者在另一个本地的 branch 进行后续的翻译
4. 更新（创建）PR 时，请更新 labels，方便管理

