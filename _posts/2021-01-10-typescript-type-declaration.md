---
layout: post
title: "TypeScript Type Declaration"
date: 2021-01-10 16:30
categories: post
tags: [typescript, tsconfig.json, declaration, d.ts]
comments: true
---

# 타입 선언 자동 생성

`tsconfig.json` 파일에 아래와 같이 옵션 2개를 설정합니다.

```json
{
  "compilerOptions": {
    "declaration": true,
    "declarationDir": "@types",
    ...
  },
}
```

`tsc` 명령어 컴파일하면 `tsconfig.json` 파일과 같은 위치 디렉토리에 `@types` 디렉토리가 만들어지고 그 아래 `*.d.ts` 파일이 자동으로 만들어집니다.
