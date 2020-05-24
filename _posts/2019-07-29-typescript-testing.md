---
layout: post
title: "TypeScript Basic"
date: 2019-07-29 00:00
categories: post
tags: [tech, typescript, basic]
comments: true
---

## Types

### Basic Types
 - boolean
 - number
 - string
 - [], Array<Type>
 - [Type, Type]
 - {,,,}
 - any, any[]
 - void
 - undefined, null
 - naver


#### Boolean
```
let isDone: boolean = false;
```

#### Number
```
let decimal: number = 6;
```


#### String
```
let color: string = "blue";
```


#### Array
```
let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3];
```


#### Tuple
```
let x: [string, number];

```


#### Enum
```
enum Color {Red, Green, Blue}
let c Color = Color.Green;
```


#### Any
```
let notSure: any = 4;
let list: any[] = [1, true, "free"];
```


#### Void
```
let unusable: void = undefined;
```


#### Null and Undefined
```
let u: undefined = undefined;
let n: null = null;
```


#### Never
```
function error(message: string): never {
    throw new Error(message);
}
function infiniteLoop(): never {
    while (true) {
    }
}

```


#### Object
```
declare function create(o: object | null): void;

create({ prop: 0 }); // OK
create(null); // OK

create(42); // Error
create("string"); // Error
create(false); // Error
create(undefined); // Error
```
