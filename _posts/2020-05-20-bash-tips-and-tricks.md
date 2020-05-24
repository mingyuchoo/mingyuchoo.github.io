---
layout: post
title: "Bash Tips & Tricks"
date: 2020-05-24 00:00
categories: post
tags: [tech, bash]
comments: true
---

### 한 번에 모든 프로젝트에 ncu 로 모듈 업데이트하기

```bash
for directory in $(ls)
do
  pushd $directory
  cd $directory
  ncu -u
  popd
done
```

### 특정 디렉터리의 자식 디렉터리를 탐색하며 특정 파일을 삭제하기

```bash
for directory in $(ls)
do
  pushd $directory
  cd $directory
  rm package-lock.json
  popd
done
```

### Java 프로세스 목록 Kill

```bash
for pid in $(ps aux | grep java | awk '{print $2}')
do
  kill $pid
done
```

### 메모리 사용량 순서로 프로세스 목록 보기

```bash
ps -ef --sort -rss | head -n 11
```
