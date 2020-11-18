# Vue组件 :lion:

组件是可复用的Vue实例，在Vue根实例中可以把组件作为自定义元素来使用。

组件中的data必须是一个函数

```js
// 页面中
data: {
  count: 0
}
// 组件中
data: function () {
  return {
    count: 0
  }
}
```

#### 组件名 :lion:

命名方式有两种

- kebab-case  <my-component>
- PascalCase  <myComponent>

#### 全局注册 :lion:

好处是在任何新创建的Vue的根实例中使用

#### 局部注册 :lion:

全局注册在模块式开发时，意味着你已经不再使用一个组件了，它会被包含在最终的构建结果中（即使你不使用一样会被加载）。造成了用户下载JavaScript的负担。

**局部注册的组件在其子组件中不可用**，可以使用import来引入。

#### prop :lion:

由于HTML中对于标签名大小写是不敏感的，所以一般使用kebab-case命名方式。

##### prop类型 :lion:

