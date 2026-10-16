Next.js 支持API Routes，可以让我们在Next.js中创建API端口



```typescript
export default (req, res) => {
  res.status(200).json({ text: 'Hello' })
}
```



注：不要从getStaticProps或getStaticPaths获取API Routes