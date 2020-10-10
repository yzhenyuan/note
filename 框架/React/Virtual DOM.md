# Virtual DOM是什么？


1. vdom是一种编程概念，他实际上就是一个js对象，包含了 tag、props、children 三个属性
2. 因为真实的 DOM操作很慢，轻微的操作都可能导致⻚面重新排版，⾮常耗性能
    + 仅仅创建一个div就会有很多属性值，
    + 由于 DOM 操作的复杂性，Virtual DOM被创造了出来，
    + 他以一个虚拟树的状态，存储在内存中，再映射到真实的 DOM，
    + 每次更新，都是虚拟树的对比，再将差异部分进行更新，并反映到真实 DOM 上去，这样我们就减少了对真实 DOM 的操作。
3. 虚拟DOM提高性能，不是说不操作DOM，而是减少操作DOM的次数，减少回流和重绘
```
<div id="app">
  <p class="text">hello world!!!</p>
</div>

转换为虚拟 DOM 如下：

{
  tag: 'div',
  props: {
    id: 'app'
  },
  chidren: [
    {
      tag: 'p',
      props: {
        className: 'text'
      },
      chidren: [
        'hello world!!!'
      ]
    }
  ]
}

```


## 为什么更新 DOM 很慢

操作DOM的过程，例如：
```
document.getElementById('elementId').innerHTML="New Value"
```
1. 浏览器必须解析HTML
2. 它删除了elementId 的子元素
3. 使用"New Value"更新DOM
4. 重新计算父和子的CSS
5. 更新布局，即每个元素在屏幕上的精确坐标
6. 遍历渲染树并在浏览器显示上绘制它


重新计算CSS和更改布局使用复杂的算法，它们会影响性能。  
因此，更新真正的DOM并不仅仅涉及更新DOM，而是涉及许多其他过程。  
此外，上述每个步骤都针对真实DOM的每次更新运行，即如果我们更新真实DOM 10次，则上述步骤中的每一个将重复10次。  
这就是为什么更新 DOM 很慢的原因。



# vdom框架的设计思路
使用 VD 的框架，一般的设计思路都是页面等于页面状态的映射，即UI = render(state)。当需要更新页面的时候，无需关心 DOM 具体的变换方式，只需要改变state即可，剩下的事情（render）将由框架代劳。我们考虑最简单的情况，当 state 发生变化时，我们重新生成整个 VD ，触发比较的操作。上述过程分为以下四步： 
- state 变化，生成新的 VD 
- 比较 VD 与之前 VD 的异同 
- 生成差异对象（patch） 
- 遍历差异对象并更新 DOM 差异对象的数据结构是下面这个样子，与每一个 VDOM 元素一一对应：
## react的virtual dom更快
1. 高效的diff算法
2. 批量batching操作
3. 仅有效地更新子树
4. 使用可观察(observable)而不是脏检查来检测更改


## JSX
实际上，JSX 仅仅只是 React.createElement(component, props, ...children) 函数的语法糖