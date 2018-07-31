# 翻译格式与注意事项
请前往[翻译格式与建议](./style-guide.md)

# 关于 git 和 github
## 常用词汇
- repo：代码仓库
- PR：即 pull request，合并请求
- branch：分支
- commit：提交记录
- merge：指 PR 合并到代码仓库的操作
- conflicts：（合并）冲突

## 开始之前
* 首先，fork 一下 [challenges](https://github.com/FreeCodeCampChina/challenges.git) repo。

* 把**你的 fork** 克隆到本地。
  ```bash
  git clone https://github.com/your_name/challenges.git  # 注意，`your_name` 是你的 github ID。
  ```
* 切换到 challenges 文件夹。
  ```bash
  cd challenges
  ```
* 根据你在翻译的项目名称或者你正在做的事情，新建分支。
  ```bash
  # 建议每次都从 translate 分支建立新的分支
  # 请参考后面的“常见问题”
  git checkout -b your_branch_name  #  `your_branch_name` 是你的分支名
  ```
* 在本地进行代码或文件修改。

* 添加要追踪的文件到暂存区。
  ```bash
  git add .        # 注：这个命令不是永远都会添加你的所有改动，请参考“常见问题”。
  git add my.json  # 或者你也可以添加某一个文件
  ```
* 提交 commit 到本地仓库。
  ```bash
  git commit -m "My commit message"  # 注意，请根据实际情况填写 commit message。
  git commit # 或者你也可以打开你喜欢的编辑器（需要配置），在里面编写 commit message。
  ```
* 把本地仓库推送到远程仓库。
  ```bash
  git push origin your_branch_name
  ```
* 打开 github 页面，创建 PR。

## 同步远程更新至本地
* 关联上游 repo 至本地项目。
  ```bash
  git remote add upstream https://github.com/FreeCodeCampChina/challenges.git
  ```
* 获取上游更新，并应用到本地。
  ```bash
  git pull --rebase upstream translate
  ```

## 注意
* `pull` 或 `rebase` 之后，如果有 conflicts，可以先使用 `git status` 查看存在 conflicts 的文件。

  修改成需要的版本后，使用 `git add .` 然后 `git rebase --continue`。
  
  **请注意，在这个过程中：不要 commit！不要 commit！不要 commit！**
   
* 解决冲突之后，需要更新至远程，否则只有你的本地有更新。
  ```bash
  git push origin your_branch_name
  ```
* 如果出现错误提示，请先使用 `git status` 命令检查本地是否有未解决完成的 conflicts。

* 任何时候出现错误，不必惊慌。

  先使用 `git status` 命令检查当前所在的分支、当前目录是否纯净（clean），以及本地是否有未解决完成的 conflicts。

* 如果上一步没问题，你可以用 `git push -f origin your_branch_name` 来更新远程。

* 如果你已经用当前的 branch 开了 PR，那么更新这个 branch 至远程的同时，你的 PR 也会自动更新。

## 常见问题
<details><summary><b>为什么 "git add ." 命令有时会添加不上我的改动？</b></summary>

  注意，`git add .` 中的 `.` 表示“当前路径”。

  因此，如果你通过 `cd` 命令切换到子目录，并在里面执行 `git add .`，那么外面的改动则不会添加。

  然而，如果你在父级目录执行 `git add .`，子级目录里的文件改动是会添加的。

  真正的“添加所有文件”的命令是 `git add --all`，可以简写为 `git add -A`。

  对于这个翻译项目，我们很少会需要 `cd` 进子目录。因此，一般情况下使用 `git add .` 就足够了。

</details>

<details><summary><b>如何解决冲突？</b></summary>

  对于任何多人协作项目，有 merge conflicts 是十分正常的。

  如果你在命令行中看到了 `CONFLICTS` 这样的输出，那就表示有冲突。

  这时，你需要先使用 `git status` 命令来查看冲突发生的文件。

  一般来说，有冲突的文件会显示成这样：

  ```text
  some code ....（这里的代码是没有冲突的）
  <<<<<<< HEAD
  code version 1
  code version 1
  =======
  code version 2
  code version 2
  >>>>>>> your_branch_name
  yet some other code ....（这里的代码也是没有冲突的）
  ```

  注意，里面的 `HEAD` 和 `your_branch_name` 位置可能互换，也可能会是其他内容，比如一个 commit hash。

  其中，`<<<<<<<` 与 `=======` 之间为代码的一个版本，`=======` 与 `>>>>>>>` 之间为代码的另一个版本。

  你需要来决定使用哪个版本的代码，修改的时候，把 `<<<<<<<`、`=======` 和 `>>>>>>>` 这三行都删掉。

  以及，删掉你不需要的那个版本，保留你需要的版本。

  处理完所有的冲突文件后，（由于我们执行的是 `git pull --rebase`），那么我们需要 `git add .`，然后 `git rebase --continue`。

</details>

<details><summary><b>如果某个文件我没有改动，在处理冲突的时候如何可以使用 upstream 上 translate 分支的版本？</b></summary>

  有时，可能会存在你没修改某个文件的内容，然而它却出现在了 conflicts 里（特别是如果你之前使用过 `pull`，而不是 `pull --rebase`）。

  这时，我们输入：。

  ```bash
  git fetch upstream
  git checkout upstream/translate -- the/path/to/that_file
  ```

  这时，你本地的这个文件就变成和远程一样了。

  处理之后，记得 `git add .`。

</details>

<details><summary><b>如何查看我当前处于哪个分支？</b></summary>

  `git branch` 可以列出本地所有的分支名，前面打星号（*）的就是你当前所在的分支。

</details>

<details><summary><b>如何切换分支？</b></summary>

  `git checkout some_branch_name` 就可以切换到对应的分支。

  以及，`git checkout -` 可以切换到上一个切换过的分支。

  在两个分支之间来回切换的时候，这个命令会很有用。

</details>

<details><summary><b>新建分支的时候，与我当前所在的分支有关联么？</b></summary>

  有，新建分支的时候，当前所在分支的所有 `commit` 也会添加到新的分支里面。

  以及，如果你本地有未 `commit` 的改动（哪怕已经 `add` 过），同样会在新建分支的时候带过去。

</details>

<details><summary><b>既然切换 branch 时代码会跟着走，我正在别的分支上翻译，突然让我去更新之前开了 PR 的另一个分支，我该怎么办？</b></summary>

  你有两个选择，`commit` 或者 `stash`：

  * `commit` 很简单，在当前分支上 `git add .` 然后 `git commit -m "xx"`，这时候你就可以使用 `checkout` 命令切换到其他分支了。

  * 在当前分支上 `git stash`，然后切换到其他分支。完成那边的更新后，切换回来，然后 `git stash pop`，你之前的代码改动就都回来了。

  需要注意的是，使用 `git stash pop` 会有丢代码的潜在风险，推荐使用 `git stash apply stash@{x}`，其中 `x` 为一个数字。

  如果你不确定你的做法是否正确，或者不了解这个命令，请在使用之前查清资料，或者在群里提问。

  **切换分支前，为防止把本地弄乱，前先使用 `git status` 来检查本地是否 “clean”。**

</details>

<details><summary><b>我可不可以根据远程的分支（比如 upstream 的 translate 分支）来创建本地分支？</b></summary>

  可以：
  ```bash
  git fetch upstream
  git checkout -b my_branch_name upstream/translate
  ```

</details>

<details><summary><b>每次都从远程创建分支太麻烦，我可不可以直接从本地创建分支？</b></summary>

  可以。建议使用本地的 translate 分支保持与 upstream 中的 translate 分支保持更新。这样做的好处是：

  * 每次新建分支的时候，切换到本地的 translate 分支，然后 `git checkout -b my_new_branch` 就好了。

  * 如果 upstream 的 translate branch 有更新，你只需要在切换到 translate 分支之后，`git pull --rebase upstream translate` 即可完成对本地 translate 分支的更新。再创建新的分支，就是基于 upstream 里最新的代码了，这样可以减少 conflicts 出现的可能。

</details>

<details><summary><b>我在一个分支上 commit 了我的代码，这时候 upstream 更新了，我该怎么做？</b></summary>

  ```bash
  git pull --rebase upstream translate
  ```

</details>

<details><summary><b>我的本地 translate 分支已经有我的 commit 了，那我该如何用这个分支作为与 upstream translate 同步的分支呢？</b></summary>

  **如果你目前在 translate 提交的内容不再需要了（比如，已经 merge），那你可以先切换到 translate，然后：**

  ```bash
  git fetch upstream
  git reset --hard upstream/translate
  ```

  虽然 `git reset` 命令不危险，但在执行这个操作之前，建议你先在群里问一下。

</details>

<details><summary><b>命令好长，我不想记。</b></summary>

  `alias` 了解一下。在命令行里执行：

  ```bash
  git config --global alias.gx 'pull --rebase upstream translate'
  ```

  下次，执行 `git gx`（记忆：git 更新），就会执行你定义好的命令了。

</details>

<details><summary><b>我已经开了 PR，但代码历史记录很乱，而且文件改动包含了不是我改的东西，如何修复？（多见于曾经在这个分支上用过 `pull` 命令，现在使用 `pull --rebase` 的情况，见下文分析）</b></summary>

  如果对 git 不是很熟悉（特别是 `git brease -i` 以及 `rebase` 命令的原理），重建一个新的分支，然后把当前这个分支里属于你的 file change 给 apply 过去，再用新的分支开 PR 是最省事的做法。
  
  假设你目前处于 `translate-old` 分支上，你改动了文件 `02-javascript-algorithms/abc.json` 以及 `02-javascript-algorithms/abc.md`，且你已经用当前的 `translate-old` 分支开了 PR：
  
  ```bash
  # 获取 upstream 的 HEAD 指针
  # （有兴趣可以去了解下 HEAD 指针是什么，这对理解 git 的原理很有帮助。但不了解也不影响后续操作）
  git fetch upstream

  # 基于 upstream 的 translate branch 新建一个 branch
  # （这一步是保证你将要提交 PR 所用的分支是基于最新的 upstream/translate 分支的代码）
  git checkout -b translate-new upstream/translate

  # 由于你这个 PR 是基于你的 translate-old 分支开的，
  # 所以现在要把这个分支上属于你的文件改动应用到新的 branch 上
  git checkout translate-old -- 02-javascript-algorithms/abc.json
  git checkout translate-old -- 02-javascript-algorithms/abc.md

  # 这个应该只输出你改过的两个文件（在这个例子中是两个）才对
  git status

  # add、commit、push
  git add .
  git commit -m "Finish translation of xxx"
  git push origin transalte-new

  # 然后用这个新的 translate-new 分支去开 PR 就好了
  ```

</details>


## 一些原则
* 建议使用 [git workflow](https://guides.github.com/introduction/flow/) 来进行分支的管理。

  这样我们可以提交 PR 之后继续在新的 branch 上进行后续的翻译，若需要更新当前的 PR，我们随时可以切换回来。
   
* 不建议同时开两个相同类型（比如翻译）的 PR，请等待之前的 merge 之后再开新的 PR。

* 如果你的 PR 已经被 review 过，请不要再添加新的翻译内容，根据 comment 修改好当前的 PR 即可。

  后续的翻译你可以等当前翻译 merge 后再开始做，或者在另一个本地的 branch 进行后续的翻译。
  
* 你的 PR 中不应包含你未改动过的文件，请在提交的时候仔细检查。如果包含了，请参考上面的解决方案。大部分情况下，坚持使用 `git pull --rebase`，不混用 `git pull` 可以在很大程度上避免这个问题的产生。

  <details><summary><b>注：包含与否一般不会影响代码库，或导致功能缺失。但这会给 review、后续的版本控制和管理造成很大的麻烦：</b></summary>

    1. Review 的时候，需要仔细比对那些本不是你改的文件，确保你没有（在 resolve conflicts 或 commit 的时候）更改任何内容。
    2. 如果你在 PR 中引入了已经 merge 的 commits，那么就会在对应的 PR 中添加对你的 PR 的 reference。事实上，由于你本无意改动那些文件，这就只会对维护者和后续的开发者造成误导。
    3. 维护者本可以直接通过文件的最新 commit 找到对应的 PR，但由于其他人也包含了这个文件，则需要一步一步排查，看究竟是哪一步出了问题。

  </details>
  
  <details><summary><b>如果你想知道产生这个问题的原因，请参考以下的图形化解释：</b></summary>

    ## 关于 PR 中，引入他人更改文件的情况分析：
    
    假设现在的 `upstream/translate` 是 `A -> B` 这两个 commits，其中 `B` 较新。你基于这个创建了你的 `my-translate` 分支，那么你也会得到 `A -> B`。
    
    之后，你开始进行翻译，并 `commit` 了代码。现在你的 `my-translate` 是 `A -> B -> X`，其中 `X` 为你的 commit。
    
    然后你发现远程更新了，现在远程是 `A -> B -> C -> D`。这次你使用了 `git pull` 命令。那么在 `my-translate` 分支，你就得到：`A -> B -> X -> M`。其中，`M` 就是传说中的 merge commit，它包含了上游的 `C` 和 `D`。
    
    （但从常理判断，这时候如果你得到 `A -> B -> C -> D -> X` 这样的历史线就更好了。这正是 `git pull --rebase` 会帮你完成的事情，以及这也是我们推荐使用这个命令的原因。）
    
    然后你继续翻译，并 `commit` 了代码，现在你的 `my-translate` 分支就是 `A -> B -> X -> M -> Y`，其中 `Y` 是你的最新 commit。
    
    这时候你执行了 `git pull --rebase`，那么问题来了。基于 `rebase` 命令的比较原理（或者说算法），它会首先寻找一个你的 `my-translate` 分支与 `upstream/translate` 分支共同的”祖先 commit“（ancestor commit）。”共同的祖先 commit“（common ancestor commit）是指这两个分支**开始出现分歧（diverted）之前的那个 commit**。在这个例子中，它就会找到 commit `B`，因为在 `B` 之后，`my-translate` 分支是 commit `X`，而 `upstream/translate` 是 commit `C`。
    
    `rebase` 的执行逻辑可以简化为 `git reset --hard` + `git cherry-pick`（好奇的朋友可以去了解下这两个命令），那么 `cherry-pick X` 的时候不会出问题（基于 `B`，添加你的翻译，显然不会有报错），但 `cherry-pick C` 的时候就很可能会出现 conflicts：
    
    假设 `C` 中，其他人更新了 `README.md`（当然，在你的 commit `X` 和 `Y` 中，你都没有修改这个 `README.md`），常理上来说，这件事**应该**发生在 `X` 之前。但由于在你的分支 `my-translate` 中，`X` 是先于 `M`（包含 `C` 和 `D`）发生的，那么这里就造成了 Git 的困扰：它觉得，根据 `upstream/translate` 分支，说好了 `B` 之后就改 `README.md` 的；然而在你的分支里，却告诉我 `B` 之后 `README.md` 不需要改，那我该怎么办？——那我就只能告诉你我遇到了 conflicts，请你手动解决下吧。
    
    这时，如果你**错误地**使用了 `git commit` 命令，那么 Git 就会觉得，这个 `README.md` 你也改动过了，事实上你并没有，以及你也没打算改，这是**我认为**导致引入他人更改文件的一种原因。
    
    后续哪怕再 `git pull --rebase`，Git 也会去找 commit `B` 作为 common ancestor。这依然会导致 conflicts，因为在 `my-translate` 里，从一开始，`B` 之后是 `X` 这件事就是错的。
    
    **我认为**的另一种可能，在这个例子中，就是如果后续还有其他人改了 `README.md` 那么本地执行 `git pull` 的时候也会产生 conflicts，这时出现的根源是 `git merge`，因为目前 `my-translate` 的 `HEAD` 显然不是那个 `README.md` 更改的 ancestor，因此 Git 没法 fast forward 那个新的 `README.md` 改动，感兴趣的朋友可以去了解下什么是 `fast-forward`。此时需要手动处理 conflicts，处理之后 `git commit`，那么 Git 就会认为你也参与到了这个 commit 中。
    
    ## 那么，`git pull --rebase` 对这种情况会有什么帮助？
    
    还是上面的例子，你的 `my-translate` 是 `A -> B -> X`，远程以及是 `A -> B -> C -> D` 了，其中 `C` 里面更改了 `README.md`。
    
    如果你采用 `git pull --rebase`，那么你的本地就会是 `A -> B -> C -> D -> X`。后续你又 `commit` 了新的代码，比如现在你的本地是 `A -> B -> C -> D -> X -> Y -> Z`。此时，远程那边也加了几个 commit，变成了 `A -> B -> C -> D -> E -> F`。
    
    如果你继续 `git pull --rebase`，那么 Git 此时寻找到的 common ancestor commit 是 `D`，而不再是上面使用 `git pull` 的 `B` 了。除非 `E` 和 `F` 里也改了你正在改的文件，否则就不太可能产生冲突。
    
    结果，你就会得到 `A -> B -> C -> D -> E -> F -> X -> Y -> Z`，这也正是我们期望的结果。
    
  </details>
  
  所以，麻烦大家花一点时间处理下。感谢 :pray:
