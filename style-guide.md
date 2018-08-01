## 开始之前
1. 到官网平台做一下（至少看一下）你打算翻译的题目，这样你会对整体内容有一个更好的把握。

2. 翻译每句话之前，先把整行句子读一遍，这可以在很大程度上避免语序错误。

3. 如果你不熟悉你需要翻译的内容，请先去 MDN 和 Wikipedia 之类的平台查资料。如果觉得有难度，请联系管理员或其他朋友换任务（不用觉得不好意思，这其实很正常）。

## 翻译完成之后
1. 通读一遍你的翻译，读的过程中，你很可能会发现错字，以及不通顺的地方。

2. 如果你是根据 review comments 更新 PR，请确保你已按照 review comments 里提到的问题更正，有些 review comments 里面提到的问题可能出现在多个地方。建议使用文本搜索工具或正则来查找。

3. 前后文要统一，标点符号、空格的使用要正确，记得检查。

## 格式
### 全角与半角
1. 翻译中不应出现全角的英文、空格和数字。

    <details><summary>示例</summary>

    :smiley: `现在我们开始学习 CSS`  
    :slightly_frowning_face: `现在我们开始学习　CSS`  
    :slightly_frowning_face: `现在我们开始学习ＣＳＳ`  

    </details>

2. 翻译中应使用全角标点（引号除外）。

    <details><summary>示例</summary>

    :smiley: `我们需要写一个函数，让它返回这两个数字间所有数字（包含这两个数字）的总和。`  
    :slightly_frowning_face: `我们需要写一个函数,让它返回这两个数字间所有数字(包含这两个数字)的总和.`  

    </details>

3. 引号的使用由引用内容决定。若引用内容全部为半角，则选用英文引号 `""`；若引用内容包含中文，则选用中文引号 `“”`。由于引号均为半角，如果引号前后为全角字符（标点除外），则需要添加空格。

    <details><summary>示例</summary>

    :smiley: `请使用 “弹性盒子”（flexbox）调整元素的布局。`  
    :smiley: `在 package.json 文件中应该有 "mongodb" 依赖`  
    :slightly_frowning_face: `请使用"弹性盒子"（flexbox）调整元素的布局。`  

    </details>

4. 破折号应使用两个 em dash，即 `——`，且两边不需要添加空格。

    <details><summary>示例</summary>

    :smiley: `有一种更好的方法——使用<code>repeat</code>。`  
    :slightly_frowning_face: `有一种更好的方法 —— 使用<code>repeat</code>。`  
    :slightly_frowning_face: `有一种更好的方法————使用<code>repeat</code>。`  

    </details>

5. 省略号应使用 `……`，或在结尾添加 `等`。

    <details><summary>示例</summary>

    :smiley: `前端开发的相关技术很多，比如 HTML、CSS、JavaScript……`  
    :smiley: `前端开发的相关技术很多，比如 HTML、CSS、JavaScript 等`  

    </details>

6. 相同的标点不应连续使用。

    <details><summary>示例</summary>

    :smiley: `今天真开心！`  
    :slightly_frowning_face: `今天真开心！！！`  

    </details>

7. 应保留代码中的英文标点。

    <details><summary>示例</summary>

    :smiley: `使用<code>Math.min()</code>来获取两数中较小的数。`  
    :slightly_frowning_face: `使用<code>Math。min（）</code>来获取两数中较小的数。`  

    </details>

8. 块级引用（blockquote）、代码块（pre）、题目 `contents` 字段里的注释部分，若不翻译则保留原符号；若需要翻译则改用全角符号。

### 结尾标点
1. 题目的描述性文字，需要在结尾添加标点。

2. 代码中的注释，原则上不需要在结尾添加标点。

### 空格
1. 全角与半角内容之间需要加空格。注意：**内容指的是文字内容，不是标点符号**。

    <details><summary>示例</summary>

    :smiley: `为下列项目添加 CSS 属性`  
    :smiley: `返回值是一个长度为 2 的数组`  
    :slightly_frowning_face: `JavaScript是一种语言`  

    </details>

2. 半角字母与数字之间，不必**额外补充**空格。

    <details><summary>示例</summary>

    :smiley: `CSS3`  
    :slightly_frowning_face: `CSS 3`  

    </details>

3. 全角符号的两边不应有空格。相应地，半角字符与全角符号之间也不应添加空格。

    <details><summary>示例</summary>

    :smiley: `它接收一个查询的 document（一个 JSON 对象）作为参数。`  
    :smiley: `使用弹性盒子（flexbox）`  
    :slightly_frowning_face: `使用弹性盒子（ flexbox ）`  
    :slightly_frowning_face: `它的值应为 10 。`  

    </details>

4. HTML 标签
    1. `<br>` 之后不添加空格。

        <details><summary>示例</summary>

        :smiley: `注意<br>以下代码……`  

        </details>

    2. 行内元素如 `<a>`、`<b>`、`<dfn>`、`<strong>`，是否加空格取决于标签与外面文本，添加规则参考上文[空格 - 1](#空格)，元素中的内容也应按此标准添加。

        <details><summary>示例</summary>

        :smiley: `请参考 <a href='xxx'>Mongoose 文档</a>获取帮助。`  
        :slightly_frowning_face: `父级元素叫做<dfn>container</dfn>`  

        </details>

    3. `<code>` 标签，无论全半角，任何情况都不添加空格。

        <details><summary>示例</summary>

        :smiley: `使用<code>mongoose.connect</code>命令来连接数据库。`  

        </details>

## 翻译原则
1. 追求意译，不要逐字逐句翻译。可以根据上下文对内容进行必要的补充。

    <details><summary>示例（有关测试结果的提示信息）</summary>
    原文：`You can return the array with its elements in any order.`

    :slightly_frowning_face: `你可以返回一个数组，这个数组中的元素顺序无所谓`  
    :slightly_frowning_face: `你可以返回一个元素有任意顺序的数组`  
    :smiley: `返回数组中的元素顺序不会影响测试结果`  

    </details>

    <details><summary>示例</summary>
    原文：`JavaScript is important, well, you know.`

    :slightly_frowning_face: `JavaScript 很重要，那么，你知道的。`  
    :smiley: `你知道的，JavaScript 很重要。`  
    :smiley: `JavaScript 很重要，你懂的。`  

    </details>

2. 尽可能地采用书面语。

    <details><summary>示例</summary>
    原文：`Learning JavaScript is fun!`

    :slightly_frowning_face: `学 JavaScript 真的太好玩儿了！`  
    :smiley: `学 JavaScript 很有趣！`  

    </details>

3. 如需保留原文中的英文，请核实拼写是否与官网或 Wikipedia 一致。如 `JavaScript`、`jQuery`、`React`、`MongoDB` 等。

4. 如果你确定原文的表述或格式有误，请不要按照错误的内容翻译，以免造成误导。如果你不确定，可以把内容放到群里跟大家一起讨论。当然，发现错误后，你也最好给原版的 repo 开一个 issue 或 PR。

## 中英有别
1. 英文与中文的句号用法不同。在翻译的时候，有时我们需要把多个句子合并成一句。

    <details><summary>示例</summary>
    原文：`JavaScript is a high-level, interpreted programming language. It is a language which is also characterized as dynamic and weakly typed.`

    :slightly_frowning_face: `JavaScript 是一种高级、解释型的编程语言。它有动态和弱类型的特点。`  
    :smiley: `JavaScript 是一种动态、弱类型、解释型的高级编程语言。`  

    </details>

2. 英文中的 `a` 和 `an` 有时候不表示数量，而是泛指。此时不应翻译成“一个”。

    <details><summary>示例</summary>
    原文：`Use CSS to position an element in a flexible way.`

    :slightly_frowning_face: `以一种灵活的方式使用 CSS 去布局一个元素。`  
    :smiley: `灵活地使用 CSS 布局元素。`  

    </details>

3. 英文中习惯使用被动语态，中文则习惯使用主动语态。

    <details><summary>示例</summary>
    原文：`The direction that child items are arranged is called the main axis.`

    :slightly_frowning_face: `子元素排列的方向被称为主轴。`  
    :smiley: `子元素排列的方向叫做主轴。`  

    </details>

4. 英文中经常出现从句（构成复杂句），翻译的时候可以适当地补充主语或宾语。

    <details><summary>示例</summary>
    原文：`Media Queries are a new technique introduced in CSS3 that change the presentation of content based on different viewport sizes.`

    :slightly_frowning_face: `媒体查询是 CSS3 中引入的一项可以根据不同的可视窗口大小来显示不同布局的新技术。`  
    :smiley: `媒体查询是 CSS3 中引入的一项新技术，它可以根据不同的可视窗口大小来调整页面布局。`  

    </details>

4. 英文中经常出现从句（构成复杂句），翻译的时候可以适当地补充主语或宾语。

    <details><summary>示例</summary>
    原文：`Media Queries are a new technique introduced in CSS3 that change the presentation of content based on different viewport sizes.`

    :slightly_frowning_face: `媒体查询是 CSS3 中引入的一项可以根据不同的可视窗口大小来显示不同布局的新技术。`  
    :smiley: `媒体查询是 CSS3 中引入的一项新技术，它可以根据不同的可视窗口大小来调整页面布局。`  

    </details>

5. 英文中的时态有时不必刻意翻译出来。

    <details><summary>示例</summary>
    原文：`The lowest number will not always come first.`

    :slightly_frowning_face: `最小的数将不会总是出现在数组的第一个元素。`  
    :smiley: `较小数不一定总是出现在数组的第一个元素。`  

    </details>

6. 尽量避免双重否定。注意：不一定要出现 `not` 才是否定。

    <details><summary>示例</summary>
    原文：`There isn't no other way.`

    :slightly_frowning_face: `并不是没有其他办法。`  
    :smiley: `总会有其他办法的。`  

    </details>

    <details><summary>示例</summary>
    原文：`Few people would not like to do it.`

    :slightly_frowning_face: `一些人会不愿意做这件事。`  
    :slightly_frowning_face: `很少有人会不愿意做这件事。`  
    :smiley: `大部分人都愿意做这件事。`  

    </details>

7. 适当地调整语序，特别是英文中补充说明的部分。

    <details><summary>示例</summary>
    原文：`HTML and CSS, constructs the web page together with JavaScript.`

    :slightly_frowning_face: `HTML 和 CSS，一起构成了页面，与 JavaScript 一起。`  
    :smiley: `HTML、CSS 与 JavaScript 一同构成页面。`  

    </details>

8. 英文的分词（participle）有时并不表示时态，尤其是在表示状态的时候。

    <details><summary>示例</summary>
    原文：`Once done, you may continue to the next challenge.`

    :slightly_frowning_face: `当现在的挑战被完成了，你就可以继续做下一个了。`  
    :smiley: `完成当前的挑战之后，你就可以继续做下一个了。`  

    </details>

9. 对于多项列举，英文采用逗号分隔，并在最后一个之前加 `and`，或在结尾加 `, etc.`。中文则用顿号分隔，且不要求结尾加“和”。

    <details><summary>示例</summary>
    原文：`HTML, CSS and JavaScript are fundamental knowledge for web developers.`

    :slightly_frowning_face: `HTML，CSS 和 JavaScript 是前端开发的基础。`  
    :smiley: `HTML、CSS、JavaScript 是前端开发的基础。`  

    </details>

10. 英文中的同位结构（apposition）一般不必单独翻译，可以合并。注意，同位结构多出现于两逗号之间。但出现在两逗号之间的**不一定是**同位结构，也可以是插入语或复合句的从句。

    <details><summary>示例</summary>
    原文：`My instructor, John, is a nice guy.`

    :slightly_frowning_face: `我的导师，约翰，是个好人。`  
    :smiley: `我的导师约翰是个好人。`  


    </details>

