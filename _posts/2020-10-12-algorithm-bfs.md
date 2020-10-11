---
layout: post
title: "BFS"
date: 2020-10-12 03:30
categories: post
tags: [algorithm, bfs]
comments: true
---


# BFS(깊이 우선 탐색, Breadth First Search)

## 정의

Breadth First Search의 약자로 너비 우선 탐색을 뜻한다. 버텍스(vertex)의 형제들(siblings)을 우선으로 탐색한다.

## 유형 특징

거의 빠지지 않고 출제된다.
기본 코드를 외우고 들어가는 것이 좋다.

## 문제 식별

현재 위치에서 뻗어 나가되, 영역(DFS)보다 거리(BFS)를 목표로 할 때 적용할 수 있다. 

상하좌우로 좌표를 이동하여 미로를 탈출하는 게임인데 목표가 최소 이동 수를 구는 상황일 때 적용할 수 있다. 


## 출제 특징

상하좌우, 동서남북, 등의 좌표가 제시되는 경우가 많다.

제시된 공간을 넘어갈 때 처리하는 상황이 주어질 수 있다.

## 예제

- 미로 출구까지의 거리 구하기
- 특정 거리의 도시 찾기
