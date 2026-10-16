概念：Pipe（管道）可以将输入数据转换为所需的输出。此外，它也可以处理验证，当数据不正确时可能会抛出异常。

注：nest自带部分管道

实现：

```typescript
// parse-int.pipe.ts 将字符串转换为数字, 并且对非数字抛出异常
import { PipeTransform, Injectable, ArgumentMetadata, BadRequestException } from '@nestjs/common';
@Injectable()
export class ParseIntPipe implements PipeTransform<string> {
  async transform(value: string, metadata: ArgumentMetadata) {
    const val = parseInt(value, 10);
    if (isNaN(val)) {
      throw new BadRequestException('Validation failed'); // 抛出异常
    }
    return val;
  }
}

// 全局使用 main.ts
import { ParseIntPipe } from './parse-int.pipe.ts';
async function bootstrap() {
  ...
  app.useGlobalPipes(new ParseIntPipe());
  ...
}

// 局部使用 module.controller.ts
import { ParseIntPipe } from '@nestjs/common'; // nest自带部分管道
...
@Patch(':id')
update(@Param('id', new ParseIntPipe()) id): string {
    ...
}
```

