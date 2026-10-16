类型定义：

```typescript
React.FC<Props> | React.FunctionComponent<Props> // 表示函数组件类型
React.Component<Props, State> // 表示class组件类型
React.ComponentType<Props> // 表示(React.FC|React.Component)的集合
React.ReactElement | JSX.Elemnt // 表示一个原生DOM组件(如<div /> 或 用户自定义组件)
React.ReactNode // 表示任意react节点(相当于ReactElement包括Fragments和Portals) + 原始JS类型)
React.CSSProperties // 表示JSX中样式对象的类型
React.HTMLProps<HTMLXXXElement> // 表示指定HTML元素类型(如: React.HTMLInputElement)
React.ReactEventHandler<HTMLXXXElement> // 表示event handler(事件处理程序)的泛型类型
React.XXXEvent<HTMLXXXElement> //表示更多特殊的event
// 例如: changeEvent, FormEvent, FocusEvent, KeyBoardEvent, MouseEvent, DragEvent, PointerEvent, WheelEvent, TouchEvent
```

