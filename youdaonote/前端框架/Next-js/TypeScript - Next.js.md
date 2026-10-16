静态生成和服务器端渲染：

```typescript
import { GetStaticProps, GetStaticPaths, GetServerSideProps } from 'next'

export const getStaticProps: GetStaticProps = async context => {
  // ...
}
export const getStaticPaths: GetStaticPaths = async () => {
  // ...
}
export const getServerSideProps: GetServerSideProps = async context => {
  // ...
}
```



API Router:

```typescript
import { NextApiRequest, NextApiResponse } from 'next'

export default (req: NextApiRequest, res: NextApiResponse) => {
  // ...
}
```



自定义 “APP”:

```typescript
import { AppProps } from 'next/app'

function App({ Component, pageProps }: AppProps) {
  return <Component {...pageProps} />
}

export default App
```

