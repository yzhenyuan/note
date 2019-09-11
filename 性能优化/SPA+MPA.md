#### MPA多页系统  
```
webpack+nodejs+swig  
后端数据输出  
```
> 优势：

1. 直接在前端页面输出后台变量
2. 可以做直出 ssr
3. bigpipe分段请求数据
4. 相互之间的切页 可见可操做  

> 缺点

1. 资源重复加载
2. 相互之间的开发成本稍微大，真路由和假路由碰到一起


#### SPA单页系统  
```
vue-router/react-router  
没有后端  
pushstate  
被JavaScript拦截，对应输出数据
```
> 优势：

    切页的成本最小，局部刷新比较快

> 缺点

     MPA优点

处理切页
代理a链接  

如果是站内跳转：给一段ajax里面有  HTML 、CSS 、js  
站外：刷新、实施多页 ssr/seo 

通过请求头判断站内和站外
    

