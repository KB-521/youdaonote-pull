概念：路由守卫。

实现：

```typescript
/* 简单的身份判断 */
// roles.guard.ts 定义守卫逻辑
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}
  canActivate(context: ExecutionContext): boolean {
    // 拿到映射的可访问权限
    const roles = this.reflector.get<string[]>('roles', context.getHandler());
    if (!roles) return true;
    // 取出请求端权限
    const request = context.switchToHttp().getRequest();
    const { user } = request.query; 
    // 逻辑处理，最后return出一个布尔值
    ...
  }
}

// roles.decorator.ts 映射可访问权限逻辑
import { SetMetadata } from '@nestjs/common';
export const Roles = (...roles: string[]) => SetMetadata('roles', roles);

// 局部使用 module.controller.ts
import { Roles } from './roles.decorator';
import { RolesGuard } from './roles.guard';
@UseGuards(RolesGuard)
@Controller('/module')
export class ModuleController {
  constructor(private readonly roleGuardService: RoleGuardService) {}
  @Get()
  @Roles('admin') // 映射可访问权限
  fetch(@Query() { id }): string {
    ...
  }
}
```

