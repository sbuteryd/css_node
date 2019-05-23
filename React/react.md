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

```$xslt

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