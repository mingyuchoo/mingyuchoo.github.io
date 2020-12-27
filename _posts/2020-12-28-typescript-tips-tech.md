---
layout: post
title: "TypeScript Tips & Tech"
date: 2020-12-28 04:43
categories: post
tags: [typescript, d.ts, module]
comments: true
---

# `*.d.ts` 파일 안에 있는 타입과 인터페이스를 `import` 구문 없이 사용하기

- 가장 좋은 위치는 src 디렉토리와 상관없이 사용할 수 있는 그 상단 디렉토리이다.
- 그 위치에 `@types`라고 디렉토리를 만든다. 디렉토리 이름은 마음대로 정한다.
- 파일 이름은 `*.d.ts` 형태로 만든다.
- 그 내부 코드에 `declare module "<모듈명>" { ... }` 안에 타입과 인터페이스 등을 선언한다.
- `import` 구문 없이 타입과 인터페이스를 사용하고 싶으면 `declare global { ... }` 로 선언해야 한다.
