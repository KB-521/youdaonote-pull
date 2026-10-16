期约：

```javascript
let futureData = new pormise(()=>{
    //XMLHttpRequest
})
//第一次调用会返回一个对象:
{
    value: undefined, 
    state: 'pending', // 状态码
    onFuifulled: [], // 成功时调用里面所有的函数
    onrejected: [] // 失败时调用里面所有的函数
}
futureData.then(Fun); //将Fun函数传入onFuifull;
// 当value改变state里的值会变成'resolved', 并会将value当做参数,执行onFuifulled里的所有函数。
```



源码实现：

```javascript
const PENDING = "pending"
const RESOLVED = "resolved"
const REJECTED = "rejected"
// promise构造函数
function MyPromise(fn) { // fu = 传入的函数
  const _this = this
  _this.currentState = PENDING
  _this.value = undefined
  // 用户储存 then 中的回调，只有pending转态是才会缓存
  _this.onResolvedArr = []
  _this.onRejectedArr = []
  // 创建resolved 和 rejected 函数
  function resolved(value) {
    setTimeout(function () {
      if (_this.currentState === PENDING) {
        _this.currentState = RESOLVED
        _this.value = value
        _this.onResolvedArr.forEach(cb => cb())
      }
    }, 0)
  }
  function rejected(error) {
    setTimeout(function () {
      if (_this.currentState === PENDING) {
        _this.currentState = REJECTED
        _this.value = error
        _this.onRejectedArr.forEach(cb => cb())
      }
    }, 0)
  }
  // 执行fn
  fn(resolved, rejected)
}
// 加入.then()方法
MyPromise.prototype.then = function (onResolved, onRejected) {
  let promise2
  const _this = this
  // 保证传入的是函数
  onResolved = typeof onResolved === "function" ? onResolved : function (value) {
    return value
  }
  onRejected = typeof onRejected === "function" ? onRejected : function (err) {
    return err
  }
  // 有结果的情况下以及重复调用.then触发
  if (this.currentState === RESOLVED) {
    return (promise2 = new MyPromise(function (resolved, rejected) {
      let x = onResolved(_this.value);
      if (x instanceof MyPromise) {
        x.then(resolved, rejected)
      } else {
        resolved(x)
      }
    }))
  }
  if (this.currentState === REJECTED) {
    return (promise2 = new MyPromise(function (resolved, rejected) {
      let x = onRejected(_this.value);
      if (x instanceof MyPromise) {
        x.then(resolved, rejected)
      } else {
        resolved(x)
      }
    }))
  }
  // 状态是 pending 的话给把函数推入对应数组
  if (this.currentState === PENDING) {
    return (promise2 = new MyPromise(function (resolved, rejected) {
      _this.onResolvedArr.push(function () {
        let x = onResolved(_this.value);
        if (x instanceof MyPromise) {
          x.then(resolved, rejected)
        } else {
          resolved(x)
        }
      })
      _this.onRejectedArr.push(function () {
        let x = onRejected(_this.value);
        if (x instanceof MyPromise) {
          x.then(resolved, rejected)
        } else {
          resolved(x)
        }
      })
    }))
  }
}
```

