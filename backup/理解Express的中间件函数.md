**当使用Express框架时，next函数用于将控制权传递给下一个中间件函数。
下面是一个简单的示例，演示了如何使用next函数：**

```javascript
const express = require('express');
const app = express();

// 中间件函数1
app.use(function (req, res, next) {
  console.log('中间件函数1');
  // 调用next函数将控制权传递给下一个中间件函数
  next();
});

// 中间件函数2
app.use(function (req, res, next) {
  console.log('中间件函数2');
  // 调用next函数将控制权传递给下一个中间件函数
  next();
});

// 路由处理函数
app.get('/', function (req, res) {
  console.log('路由处理函数');
  res.send('Hello World!');
});

app.listen(3000, function () {
  console.log('应用已启动在 http://localhost:3000');
});
```

**在上述示例中，我们定义了两个中间件函数和一个路由处理函数。
每个中间件函数都会在请求到达时被调用，并且可以使用next函数将控制权传递给下一个中间件函数。

当我们访问根URL时，这是一个GET请求，
首先中间件函数1会被调用，
然后中间件函数2会被调用，
最后才会执行路由处理函数。
在每个中间件函数中，我们使用console.log来打印一条消息。可以在控制台中查看这些消息的输出顺序。

注意，如果在中间件函数中不调用next函数，
控制权将不会传递给下一个中间件函数或路由处理函数，
请求处理过程会被中断，并且客户端可能会一直处于等待状态。
因此，确保在适当的时候调用next函数是很重要的。**