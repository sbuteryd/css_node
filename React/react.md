

我们总结下我们在这节课介绍的关于为何 React 很强大的知识：

它的函数组合模型
它的声明式特性
数据从父组件流向子组件的方式
以及 React 本质上就是 JavaScript


### 1-2 什么是函数组合？

根据维基百科的定义，函数组合是:

将简单的函数组合到一起并形成复杂的函数

函数组合的优势
因为函数组合是让 React 非常强大的重要原因之一，因此我们将深入了解这一概念。注意，函数组合就是将简单的函数组合到一起，并形成复杂的函数。
有几个重要概念值得注意，包括：

简单的函数
组合到一起形成另一个函数

```$xslt
function getProfileLink (username) {
  return 'https://github.com/' + username
}
```

```$xslt
function getProfilePic (username) {
  return 'https://github.com/' + username + '.png?size=200'
}
```

这个函数_极为简单，对吧？只有一行！类似地，getProfilePic 函数也_只有一行：

```$xslt
function getProfileData (username) {
  return {
    pic: getProfilePic(username),
    link: getProfileLink(username)
  }
}
```

我们可以不用组合形成 getProfileData，而是直接向其提供数据(function getProfileLink )：
理论上来说，根本没有问题；这完全是正确的 JavaScript 代码。但_不是_函数组合。

[getProfileLink 单个函数，在多个地方都可以使用，这样做了多件事]

#### 好的函数应该遵守"DOT”规则：

只做一件事

这个函数做了好几件事（无论有多小）；

创建两个不同的 URL，将它们存储为对象上的某个属性，然后返回该属性。在组合版本中，每个函数只做一件事：

getProfileLink – 只构建用户的 GitHub 个人资料链接字符串

getProfilePic – 只构建用户的 GitHub 个人资料照片字符串

getProfileData – 返回新的对象


函数组合总结

函数组合是指将_简单的函数组合到一起并形成更复杂的函数。
可以将每个函数看做一个只做一件事_ (DOT)的构建模块。
当你将这些简单的函数组合到一起并形成更复杂的函数时，这就叫做函数组合。

[核心思想一个函数做一件事情然后把函数组合起来]

[以下代码每个函数做了多件事情,查找id，替换、添加]

```$xslt
function createEelemnt(inputHeight,inputWeight){
    let pixelCanvas = document.getElementById('pixelCanvas');
    for(let i=0;i<inputHeight;i++){
        let row = pixelCanvas.insertRow(-1);
        for(let y=0;y<inputWeight;y++){
           let cell= row.insertCell(0)
        }
    }
}

const container = document.querySelector('#container');//1
container.addEventListener('click',pixClick);
```

### 1-3  什么是声明式代码？

#### 命令式代码
很多 JavaScript 都是命令式代码。如果你不知道这里的“命令式”是什么意思，那么可能会比较头疼。

根据字典的定义，“命令式”是指：
表示一项命令；下达命令

如果将 JavaScript 代码写成命令式，则我们是在明确地告诉 JavaScript 做什么，如何执行。
[每个代码自己都看的到，是怎么执行到]
可以看做我们命令 JavaScript 明确执行哪些步骤。例如，下方的一个简单 for 循环：

```$xslt
const people = ['Amanda', 'Geoff', 'Michael', 'Richard', 'Ryan', 'Tyler']
const excitedPeople = []

for (let i = 0; i < people.length; i++) {
  excitedPeople[i] = people[i] + '!'
}
```

但这是命令式代码。我们命令 JavaScript 在每一步执行什么操作。我们需要给它下达命令：
### 1-2 声明式代码

与命令式代码相反的是声明式代码。对于声明式代码，我们不编写所有步骤来获得最终结果。相反，我们_声明_要完成的操作，JavaScript 将帮助我们执行它。这种解释有点抽象，我们来看个示例。我们将刚刚查看的命令式 for 循环代码变得更加声明式。

对于命令式代码，我们执行所有步骤来获得最终结果。但是，我们实际上希望达到什么样的最终结果？起始点是名称数组：

```$xslt
const people = ['Amanda', 'Geoff', 'Michael', 'Richard', 'Ryan', 'Tyler']
const excitedPeople = people.map(name => name + '!')

```
[我要到结果给我，过程不重要]

就是这样！注意，对于这段代码，我们没有：

创建迭代器对象
告诉代码何时应该停止运行
使用迭代器访问 people 数组中的特定项
将每个新字符串存储在 excitedPeople 数组中
...所有这些步骤都由 JavaScript 的 .map() 数组方法来完成。


### 1-3  React 是声明式
```$xslt
<button onClick={activateTeleporter}>Activate Teleporter</button>
```
你可能觉得奇怪，但这段代码是有效的 React 代码，应该很容易理解。

注意，按钮只有一个 onClick 属性... 

我们没有使用 .addEventListener() 并利用所有涉及的步骤来设置事件处理过程。

我们只是声明我们希望在按钮被点击时，运行 activateTeleporter 函数。

声明式代码总结

命令式代码告诉 JavaScript _如何执行每个步骤。对于声明式代码，我们告诉 JavaScript 我们希望实现什么结果_，让 JavaScript 处理每个步骤。

React 是声明式代码，因为我们编写代码来声明我们想要什么，React 负责处理声明的代码，并执行所有的 JavaScript/DOM 步骤来实现我们期望的结果。


### 1-4 单向数据流

React 的数据流
对于 React 的单向数据流，数据移动方向不一样。在 React 中，数据从父组件流向子组件。

![数据流](image/react_data.jpg)

在上图中有两个组件：

一个父组件
一个子组件

数据位于父组件中，并向下传递给子组件。虽然数据位于父组件中，但是父组件和子组件都可以使用数据。

然而，如果必须更新数据的话，则只有父组件应该进行更新。

如果子组件需要更改数据，它会将更新的数据发送给父组件，由父组件完成更改。

父组件执行更改后，会将更新的数据传递给子组件。

听起来可能觉得带来了额外的工作量，但是让数据朝着一个方向流动并在一个位置修改使我们更容易理解应用的工作原理。


```$xslt
<FlightPlanner>
  <DatePicker />
  <DestinationPicker />
</FlightPlanner>
```
FlightPlanner,组件应该负责对数据做出更新


```$xslt
<FlightPlanner>

  <LocationPicker>
    <OriginPicker />
    <DestinationPicker />
  </LocationPicker>

  <DatePicker />

</FlightPlanner>
```

FlightPlanner,LocationPicker,负责更新数据

React 中的数据流总结

在 React 中，数据仅朝一个方向流动，即从父组件流向子组件。

如果数据在兄弟子组件之间共享，那么数据应该存储在父组件中，并同时传递给需要数据的两个子组件。

### 1-5 React 就是JavaScript

#### map

React 的优势之一是你要用到的很多功能都使用的是普通的 JavaScript。

这些函数包括 .map() 和 .filter() 方法。

Array 的 .map() 方法

在现有的数组上被调用，然后根据当做参数传入的函数返回的内容返回新的数组。

因此 nameLengths 将为_新的_数组 [7, 4, 5]。

一定要理解这一点；.map() 方法返回新的数组，它没有修改原始数组。

```$xslt
const names = ['Michael', 'Ryan', 'Tyler'];
const nameLengths = names.map( name => name.length );
```

#### Array 的 .filter() 方法

在数组上被调用
传入函数作为参数
返回新的数组

.filter() 的函数用作检验条件，数组中只有通过检验的项目才会包含在新数组中。

我们看一个示例：

const names = ['Michael', 'Ryan', 'Tyler'];

const shortNames = names.filter( name => name.length < 5 );
和 .map() 一样，names 数组中的每一项都会调用传递给 .filter() 的箭头函数。

第一项（即 'Michael'）存储在 name 变量中。然后进行检验，也就是进行实际的过滤操作。
它会检查名称的长度，如果大于等于 5，那么就跳过该名称（并且不包含在新数组中！）。

但是，如果名称的长度小于 5，那么 name.length < 5 返回 true 并且该名称包含在新数组中！

最后，和 .map() 一样，.filter() 方法返回新的数组，而不是修改原始数组.

```$xslt
const shortNames = names.filter( name => name.length < 5 );
```

因此 shortNames 将为新数组 ['Ryan']。注意，现在它里面只有一个名称，因为 'Michael' 和 'Tyler' 都是 5 个字符或更长，被滤除了。

上面只是简单地介绍了 .filter() 方法的运行原理。要深入了解该方法，请访问 MDN 上的 .filter()

#### 将 .map() 和 .filter() 组合到一起

.map() 和 .filter() 的如此强大之处在于它们可以组合到一起。

因为两个方法都返回数组，因此我们可以将它们的方法调用链到一起，一个方法返回的数据可以是另一个方法的新数组。

```$xslt
const names = ['Michael', 'Ryan', 'Tyler'];

const shortNamesLengths = names.filter( name => name.length < 5 ).map( name => name.length );

```

详细讲解下，names 数组被过滤，并返回新的数组，然后对该新数组调用 .map()，

并再次返回新的数组！.map() 返回的新数组存储在 shortNamesLengths 中。


首先是 .filter()！

提醒下，你需要按照一定的顺序组合二者（先是 .filter()，然后是 .map()）。

因为 .map() 针对数组中的每项都调用一次函数，因此如果数组已经过滤过的话，运行速度会更快。


React 就是 JavaScript 总结
React 是在你已经了解的 JavaScript 基础上构建而成的！你不需要学习特殊的模板库或新的执行方式。

你将经常用的两个主要方法是：
.map()
.filter()

请务必熟练使用这两个方法，请花些时间练习使用它们。

不妨查看你的一些现有代码并尝试将你的 for 循环转换为 .map() 调用，或者看看是否能够使用 .filter() 删除任何 if 语句。