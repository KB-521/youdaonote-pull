概念：nestjs内置的集成api文档。

使用：项目运行后输入SwaggerModule.setup中设置的网址。

实现：

```typescript
// main.js
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';
 const swaggerOptions = new DocumentBuilder()
    .setTitle('标题')
    .setDescription('简介')
    .setVersion('版本号')
    .addBearerAuth()
    .build();
const document = SwaggerModule.createDocument(app, swaggerOptions);
SwaggerModule.setup('网址', app, document);

// module/classes/module.ts
import { ApiProperty } from '@nestjs/swagger';
export class Module{
  @ApiProperty({ example: '实例', description: '实例描述' })
  name: string; //传入属性名称: 类型
}

// module/dto/module.dto.ts
import { IsInt, IsString } from 'class-validator';
export class CreateCatDto {
  @IsString()
  readonly name: string;
}

// module/module.controller.ts
import { ApiResponse, ApiQuery } from '@nestjs/swagger';
import { Module } from '.classes/module';
export class ModuleController {
  ...
  @Get()
  @ApiQuery({ name: '默认测试值', required: "默认为必输"})
  @ApiResponse({
    status: 200,
    description: 'get ...',
    type: Module,
  } // 返回值实例
  ...
}
```

