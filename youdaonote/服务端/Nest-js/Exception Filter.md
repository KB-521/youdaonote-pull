概念：异常过滤，统一报错信息格式。

实现：

```typescript
// http-exception.filter.ts
import { ArgumentsHost, Catch, ExceptionFilter, HttpException } from '@nestjs/common';

@Catch(HttpException)
export class HttpExceptionFilter implements ExceptionFilter<HttpException> {
  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const response = ctx.getResponse();
    const request = ctx.getRequest();
    const status = exception.getStatus(); // 状态码
    const exceptionRes: any = exception.getResponse();
    const {
        // 取得传入内容
    } = exceptionRes;
    
    response.status(status).json({
        // 异常报错返回的值
    });
  }
}

// 全局使用 main.ts
import { HttpExceptionFilter } from './http-exception.filter';
async function bootstrap() {
  ...
  app.useGlobalFilters(new HttpExceptionFilter());
  ...
}

// 局部使用 module.controller.ts
import { HttpExceptionFilter } from './http-exception.filter';
@UseFilters(new HttpExceptionFilter()) // 局部定义
@Controller('/exception')
export class ExceptionController {
  ...
  @Get()
  fetch(@Query() { id }, @Headers('token') token): string {
    if (!id) {
      throw new HttpException(
        {
          // 传入内容
        },
        HttpStatus.BAD_REQUEST,
      );
    }
    return
  }
  ...
}
```

