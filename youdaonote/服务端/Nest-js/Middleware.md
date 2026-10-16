概念：Middleware（中间件）在路由处理程序之前调用的函数。

实现：

```typescript
// logger.middleware.ts
import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response } from 'express';

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: () => void) {
    const { method, path } = req; //路由参数
    next();
  }
}

// 全局使用 main.ts 
import { LoggerMiddleware } from './logger.middleware';
async function bootstrap() {
  ...
  app.use(LoggerMiddleware)
  ...
}

// 局部使用 app.module.ts 
import { LoggerMiddleware } from './logger.middleware';
...
export class AppModule {
  configure(consumer: MiddlewareConsumer) {
    // 为 hello 路由添加中间件
    consumer
      .apply(LoggerMiddleware)
      .exclude({ path: 'hello', method: RequestMethod.POST }) // post请求不调用中间件
      .forRoutes('hello');
  }
}

```

