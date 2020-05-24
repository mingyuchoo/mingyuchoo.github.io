---
layout: post
title: "Python Package Update"
date: 2019-07-27 00:00
categories: post
tags: [tech, python, pip]
comments: true
---

# Python 패키지 설치

## I  cannot install or upgrade pip "ssl error"

```bash
pip install --upgrade pip --trusted-host pypi.org --trusted-host files.pythonhosted.org
```

## 패키지 업데이트 하기

### 오래된 패키지 업데이트하기 1

```
pip list --outdated --format=freeze | grep -v '^\-e' | cut -d = -f 1  | xargs -n1 pip install -U
```

### 오래된 패키지 업데이트하기 2

```bash
for package in $(pip list --outdated | awk '{ print $1}')
do
    pip install $package --upgrade --trusted-host pypi.org --trusted-host files.pythonhosted.org
done
```

## requirements.txt로 부터 설치하기

```bash
pip install -r requirements.txt
```
