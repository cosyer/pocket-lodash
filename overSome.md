# lodash源码分析之overSome

本文为读 lodash 源码的第三百六十一篇，后续文章会更新到这个仓库中，欢迎 star：[pocket-lodash](https://github.com/yeyuqiudeng/pocket-lodash)

gitbook也会同步仓库的更新，gitbook地址：[pocket-lodash](https://www.gitbook.com/book/yeyuqiudeng/pocket-lodash/details)

## 依赖

```javascript
import some from './some.js'
```

[《lodash源码分析之some》](./some.md)


## 源码分析

`overSome` 接收一组断言函数 `iteratees` ，返回一个函数，在调用这个函数时，会依次调用断言函数，并将函数的参数作为断言函数的参数传入，如果其中一个断言函数返回的是真值，则得到 `true` ，否则返回 `false` 。

源码如下：

```javascript
function overSome(iteratees) {
  return function(...args) {
    return some(iteratees, (iteratee) => iteratee.apply(this, args))
  }
}
```

其实就是调用 `some` 来遍历断言函数，如果其中一个得到的是真值，则会中止遍历。

## License 

[署名-非商业性使用-禁止演绎 4.0 国际 (CC BY-NC-ND 4.0)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

最后，所有文章都会同步发送到微信公众号上，欢迎关注,欢迎提意见：  ![](https://raw.githubusercontent.com/yeyuqiudeng/resource/master/images/qrcode_front-end-article.jpg) 

作者：对角另一面 

