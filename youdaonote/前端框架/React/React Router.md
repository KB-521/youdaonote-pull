下载、引入ReactRouter：

```javascript
npm install react-router-dom --save
import {BrowserRouter,...} from "react-router-dom"
```



路由的使用：

```javascript
const routes = (
    <BrowserRouter>
        <Switch>
            <Route path="/路由名" exact={true} component={组件名} />
             //动态路由
            <Route path="/路由名/:id" component={组件名} />
        </Switch>
    </BrowserRouter>
)
//exact: 是否精准匹配路由。
//Switch: 如果放在switch里面就会从所if变成else-if。
<NavLink activeClassName="className" to="/">首页</NavLink>
//Link: 点击Link标签能改变路由。NavLink类似Link升级版,可以给一些样式
//to: 改变后的路由。exact: 是否精准匹配。
```



路由的参数：

```javascript
props.history: 里面存了一些方法,如跳转方法;
props.location: 路由的信息;
props.match.params: 动态路由带着的数据对象;
```



使用react-router-config管理路由配置：

```javascript
// src/router/index.js
const routes = [
  {
    path: "/",
    component: General, // 组件
    exact: true, // 是否精准匹配
    routes: [] // 子路由
  },
];
export default routes;

// App.jsx
import { BrowserRouter, NavLink } from 'react-router-dom';
import { renderRoutes } from 'react-router-config';
import routes from './router';

function App() {
  return (
    <BrowserRouter>
      <div>
        <NavLink to="/">首页</NavLink>
        {renderRoutes(routes)}
      </div>
    </BrowserRouter>
  );
}

// NavLink配置项: activeClassName="ink-active" // 选中样式
```



Link标签：

- 最终渲染成a标签；

- click的时候组织a标签的默认事件；

- 再取得跳转的href（即是to），用history（前端路由两种方式之一，history & hash）跳转，此时只是链接变了，并没有刷新页面。