
新建一个 chat 页面，在 `src/routes/_layout` 里面新建 `chat.tsx`
```tsx
import { Box, Container, Text } from "@chakra-ui/react";
import { createFileRoute } from "@tanstack/react-router";

import useAuth from "@/hooks/useAuth";

export const Route = createFileRoute("/_layout/chat")({
  component: Chat,
});

function Chat() {
  const { user: currentUser } = useAuth();

  return (
    <>
      <Container maxW="full">
        <Box pt={12} m={4}>
          <Text fontSize="2xl" truncate maxW="sm">
            Hi, {currentUser?.full_name || currentUser?.email} 👋🏼
          </Text>
          <Text>我是一个问答助手，可以回答你的问题</Text>
        </Box>
      </Container>
    </>
  );
}

```

在 `src\routeTree.gen.ts` 注册路由，
```ts
import { Route as LayoutChatImport } from './routes/_layout/chat'

const LayoutChatRoute = LayoutChatImport.update({
  path: '/chat',
  getParentRoute: () => LayoutRoute,
} as any)

declare module '@tanstack/react-router' {
  interface FileRoutesByPath {
    ...
    '/_layout/chat': {
      preLoaderRoute: typeof LayoutChatImport
      parentRoute: typeof LayoutImport
    }
    ...
  }
}

export const routeTree = rootRoute.addChildren([
  LayoutRoute.addChildren([
    ...
    LayoutChatRoute,
    ...
  ]),
  ...
])
```

在 `src\components\Common\SidebarItems.tsx` 的 items 列表中添加。
```tsx
const items = [
	...
  { icon: FiHome, title: "问答助手", path: "/chat" },
  ...
]
```

修改了之后需要重新构建前端
```shell
docker-compose down
```

需要重新构建前端
```shell
docker-compose build frontend
```

![|575](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250315141327660.png)

修改图标
```tsx
import { RiRobot2Line } from "react-icons/ri";

const items = [
  ...
  {
    icon: RiRobot2Line,
    title: "问答助手",
    path: "/chat",
  },
  ...
];
```

![](https://typora-birdy.oss-cn-guangzhou.aliyuncs.com/20250315142937045.png)
