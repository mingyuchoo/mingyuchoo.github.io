---
layout: post
title: "Python tips and tricks"
date: 2019-05-23 00:00
categories: post
tags: [tech, python]
comments: true
---

## 파이썬에서 Underscore( _ ) 역할
* Using in Interpreter
* Ignoring Value
* Use in Looping
* Separating Dicts of Numbers
* Naming using Underscore ( _ )
  * Single Pre Underscores **_variable**
  * Single Post Underscores **variable_**
  * Double Pre Underscores **__variable**
  * Double Pre and Post Underscores **__variable__*

## Asterisk(*)의 사용법
```python
>>> 2 * 3
6

>>> 2 ** 3
8

>>> 1.414 * 1.414
1.9993959999999997

>>> 1.414 ** 2
1.9993959999999997

# 리스트 초기화 예제
>>> zeros_list = [0] * 100
>>> zeros_list
[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

# 튜플 초기화 예제
>>> zeros_tuple = (0,) * 100
>>> zeros_tuple
(0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0)
```

## For using the variadic arguments using the asterisk(*)
```python
# A function that shows the results of running competitions consisting of 2 to 4 runners.
def save_ranking(first, second, third=None, fourth=None):
    rank = {}
    rank[1], rank[2] = first, second
    rank[3] = third if third is not None else 'Nobody'
    rank[4] = fourth if fourth is not None else 'Nobody'
    print(rank)

# Pass the 2 positional arguments
save_ranking('ming', 'alice')

# Pass the 2 positional arguments and 1 keyword argument
save_ranking('alice', 'ming', third='mike')

# Pass the 2 positional arguments and 2 keyword arguments (But, one of them was passed as like positional argument)
save_ranking('alice', 'ming', 'mike', fourth='jim')
```

## 일반 함수 인자만 사용할 경우
```python
def save_ranking(*args):
    print(args)
save_ranking('ming', 'alice', 'tom', 'wilson', 'roy')

# ['ming', 'alice', 'tom', 'wilson', 'roy']
# *a는 unpacked 상태인 리스트 또는 튜플; 형태는 value, vlaue ...
#  a는   packed 상태인 리스트 또는 튜플
```

## 키워드 함수 인자만 사용할 경우
```python
def save_ranking(**kwargs):
    print(kwargs)
save_ranking(first='ming', second='alice', fourth='wilson', third='tom', fifth='roy')

# {'first': 'ming', 'second': 'alice', 'fourth': 'wilson', 'third': 'tom', 'fifth': 'roy'}
# **a는 unpacked 상태인 딕셔너리; 형태는 key=value
#   a는   packed 상태인 딕셔너리
```

## 일반 함수 인자와 키워드 인자를 둘 다 사용할 때
```python
def save_ranking(*args, **kwargs):
    print(args)     
    print(kwargs)
save_ranking('ming', 'alice', 'tom', fourth='wilson', fifth='roy')    

# ('ming', 'alice', 'tom')
# {'fourth': 'wilson', 'fifth': 'roy'}
```

## Asterisk(*)의 컨테이너 아이템 풀기
```python
from functools import reduce

primes = [2, 3, 5, 7, 11, 13]

def product(*numbers):
    p = reduce(lambda x, y: x * y, numbers)
    return p

product(*primes)
# 30030

product(primes)
# [2, 3, 5, 7, 11, 13]
```

```python
headers = {
    'Accept': 'text/plain',
    'Content-Length': 348,
    'Host': 'http://mingrammer.com'
}  
def pre_process(**headers):
    content_length = headers['Content-Length']
    print('content length: ', content_length)
    host = headers['Host']
    if 'https' not in host:
        raise ValueError('You must use SSL for http communication')          
pre_process(**headers)
# content length:  348
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
#   File "<stdin>", line 7, in pre_process
# ValueError: You must use SSL for http communication
```

```python
numbers = [1, 2, 3, 4, 5, 6]

# The left side of unpacking should be list or tuple.

*a, = numbers
# a = [1, 2, 3, 4, 5, 6]

*a, b = numbers
# a = [1, 2, 3, 4, 5]
# b = 6

a, *b, = numbers
# a = 1
# b = [2, 3, 4, 5, 6]

a, *b, c = numbers
# a = 1
# b = [2, 3, 4, 5]
# c = 6
# 리스트 양끝에 불필요한 값을 버릴 때 사용가능하다

>>> class MyName:
...     Geeks, For, World = range(3)
...
>>> print(MyName.Geeks)
0
>>> print(MyName.For)
1
>>> print(MyName.World)
2
```

## 함수에서 여러 개의 값을 반환하기
```python
>>> def x():
...     return 1, 2, 3, 4
...
>>> a, b, c, d = x()
>>> print(a, b, c, d)
1 2 3 4
```

## 문자열 뒤바꾸기
```python
>>> a =  "codementor"
>>> print("Reverse is {}".format(a[::-1]))
Reverse is rotnemedoc
```

```python
>>> a = 'abcdefghijklmnopqrstuvwxyz'

"""reversing string with special case of slice stop param"""
>>> print(a[::-1])
zyxwvutsrqponmlkjihgfedcba

"""iterating over string contents in reverse efficiently."""
>>> for char in reversed(a):
...     print(char)
...
z
y
x
.
.
.
a

"""reversing an integer through type conversion and slicing."""
>>> num = 123456789
>>> print(int(str(num)[::-1]))
987654321
```

## 리스트 아이템 필터링
```python
>>> [*filter(lambda x: x < 4, numbers)]
[1, 2, 3]
>>>
>>> [number for number in numbers if number < 4]
[1, 2, 3]
```
## 리스트 아이템 순서 뒤바꾸기
```python
"""reversing list with special case of slice step param"""
>>> a = [5, 4, 3, 2, 1]
>>> print(a[::-1])
[1, 2, 3, 4, 5]

"""iterating over list contents in reverse efficiently."""
>>> for element in reversed(a):
...     print(element)
...
1
2
3
4
5
```

## 리스트로 이중 For Loop 구현하기
```python
>>> for x in (0,1,2,3):
...     for y in (0,1,2,3):
...         if x < y:
...             print(x,y, x*y)
...
0 1 0
0 2 0
0 3 0
1 2 2
1 3 3
2 3 6

>>> [(x, y, x*y) for x in (0,1,2,3) for y in (0,1,2,3) if x < y]
[(0, 1, 0), (0, 2, 0), (0, 3, 0), (1, 2, 2), (1, 3, 3), (2, 3, 6)]
```

## 행렬 바꾸기
```python
"""transpose 2d array [[a,b], [c,d], [e,f]] -> [[a,c,e], [b,d,f]]"""
>>> original = [['a', 'b'], ['c', 'd'], ['e', 'f']]
>>> transposed = zip(*original)
>>> print(list(transposed))
[('a', 'c', 'e'), ('b', 'd', 'f')]

"""other simple case"""
>>> mat = [[1, 2, 3], [4, 5, 6]]
>>> zip(*mat)
[(1, 4), (2, 5), (3, 6)]
```

## Store all three values of the list in 3 new variables
```python
>>> a = [1, 2, 3]
>>> x, y, z = a
>>> x
1
>>> y
2
>>> z
3
```

## List의 모든 요소를 하나의 문자열로 만들기
```python
>>> a = ["Code", "mentor", "Python", "Developer"]
>>> print " ".join(a)
Code mentor Python Developer
```

```python
"""converts list to comma separated string"""
>>> items = ['foo', 'bar', 'xyz']
>>> output = ','.join(items)
>>> type(output)
<class 'str'>
>>> print(output)
foo,bar,xyz

"""list of numbers to comma separated string"""
>>> numbers = [2, 3, 5, 10]
>>> print(','.join(map(str, numbers)))
2,3,5,10 # <class 'str'>

"""list of mix data to comma separated string"""
>>> data = [2, 'hello', 3, 3.4]
>>> print(','.join(map(str, data)))
2,hello,3,3.4 # <class 'str'>
```

## 두 개의 리스트의 행과 열을 바꾸어 출력
```python
>>> list1 = ['a', 'b', 'c', 'd']
>>> list2 = ['p', 'q', 'r', 's']
>>> for x, y in zip(list1,list2):
...    print x, y
...
a p
b q
c r
d s
```

## 한 줄로 두 개의 변수 값 교체
```python
>>> a, b = 7, 5
>>> b, a = a, b
>>> a
5
>>> b
7
```

## Loop문 없이 "codecodecodecode mentormentormentormentormentor" 문자열 출력
```python
>>> print "code"*4+' '+"mentor"*5
codecodecodecode mentormentormentormentormentor
```

## Loop문 사용하지 않고 데이터를 한 개의 리스트로 만들기
```python
>>> import itertools
>>> a = [[1,2], [3,4], [5,6]]
>>> # Output: [1,2,3,4,5,6]
>>> list(itertools.chain.from_iterable(a))
[1, 2, 3, 4, 5, 6]
```

## Checking if two words are anagrams
참고: anagram = 철자 순서를 바꾼말
```python
from collections import Counter

def is_anagram(str1, str2):
     return Counter(str1) == Counter(str2)

>>> is_anagram('abcd','dbca')
True

>>> is_anagram('abcd','dbaa')
False
```

## 외부 입력값 받기
For example “1 2 3 4 “ and return [1, 2, 3, 4]
Remember list being returned has integers in it. Don’t use more than one line of code.
```python
>>> result = map(lambda x:int(x) ,raw_input().split())
1 2 3 4
>>> result
[1, 2, 3, 4]
```

## Find the most frequent value in a list
```python
""" most frequent element in a list """
a = [1, 2, 3, 1, 2, 3, 2, 2, 4, 5, 1]
print(max(set(a), key = a.count))

""" using Counter form collections """
from collections import Counter

cnt = Counter(a)
print(cnt.most_common(3))
```

## 리스트에서 최소, 최대값의 인덱스 찾기
```python
"""Find index of Min/Max element"""
>>> print({**d1, **d2})
{'a': 1, 'b': 2}
>>> print(dict(d1.items() | d2.items()))
{'a': 1, 'b': 2}
>>> d1.update(d2)
>>> print(d1)
{'a': 1, 'b': 2}
>>>
>>>
>>> l = [40, 10, 20, 30]
>>> def minIndex(l):
...     return min(range(len(l)), key=l.__getitem__)
...
>>> def maxIndex(l):
...     return max(range(len(l)), key=l.__getitem__)
...
>>> print(minIndex(l))
1
>>> print(maxIndex(l))
0
```

## Chained Comparison
```python
>>> """chained comparison with all kind of operators"""
>>> print(4 < b < 7)
True
>>> print(1 == b < 20)
False
```

## 리스트에서 중복된 값 제거
```python
"""remove duplicate items from list. note: note preserve the original list order"""
>>> items = [2,2,3,3,1]
>>> new_items = list(set(items))
>>> print(new_items)
[1, 2, 3]

"""remove dups and keep order"""
>>> items = [2,2,3,3,1]
>>> new_items = list(set(items))
>>> print(new_items)
[1, 2, 3]
```

## Chained function call
```python
>>> """calliing different functions with same arguments based on condition"""
>>> def product(a, b):
...     return a * b
...
>>> def add(a, b):
...     return a  + b
...
>>> c = True
>>> print((product if c else add)(5, 7))
35
```

## List 복사
```python
>>> a = [5, 4, 3, 2, 1]

>>> """a fast way to make a shallow copy of a list"""
>>> b = a
>>> a
[5, 4, 3, 2, 1]
>>> b
[5, 4, 3, 2, 1]

>>> """both a and b will be [10, 2, 3, 4, 5]"""
>>> b[0] = 10
>>> a
[10, 4, 3, 2, 1]
>>> b
[10, 4, 3, 2, 1]
>>>
>>>
>>> """only b will change to [10, 4, 3, 2, 1]"""
>>> b = a[:]
>>> b[0] = 10
>>> a
[5, 4, 3, 2, 1]
>>> b
[10, 4, 3, 2, 1]
>>>
>>>
>>> """copy list by typecasting method"""
>>> a
[5, 4, 3, 2, 1]
>>> print(list(a))
[5, 4, 3, 2, 1]
>>> b = list(a)
>>> b
[5, 4, 3, 2, 1]
>>>
>>>
>>> """using the list.copy() method (python3 only)"""
>>> a
[5, 4, 3, 2, 1]
>>> b = a.copy()
>>> b
[5, 4, 3, 2, 1]
```
```python
>>> """copy nested list using copy.deepcopy"""
>>> from copy import deepcopy
>>> l1 = [[1,2], [3,4]]
>>> l2 = deepcopy(l1)
>>> print(l2)
[[1, 2], [3, 4]]
```

## Dictionary의 get 메소드 활용
```python
"""returning None or default value, when key is not in dict"""
>>> d = {'a':1, 'b':2}
>>> print(d.get('c', 3))
3
```

## 값으로 Dictionary 정렬
```python
>>> a = [5, 2, 3, 1, 4]
>>> a
[5, 2, 3, 1, 4]
>>> a.sort()
>>> a
[1, 2, 3, 4, 5]
>>>
>>>
>>>
>>> b = {1: 'D', 2: 'B', 3: 'B', 4: 'E', 5: 'A'}
>>> b
{1: 'D', 2: 'B', 3: 'B', 4: 'E', 5: 'A'}
>>> sorted(b)
[1, 2, 3, 4, 5]
>>>
>>>
>>> c = "This is a test string from Andrew"
>>> c
'This is a test string from Andrew'
>>> sorted(c.split(), key=str.lower)
['a', 'Andrew', 'from', 'is', 'string', 'test', 'This']
>>>
>>>
>>> student_tuples = [
... ('john', 'A', 15),
... ('jane', 'B', 12),
... ('dave', 'B', 10),
... ]
>>> sorted(student_tuples, key=lambda student: student[2])
[('dave', 'B', 10), ('jane', 'B', 12), ('john', 'A', 15)]
```

```python
"""Sort a dictionary by its value with the built-in sorted() function and a 'key' argument."""
>>> d = {'apple':10, 'orange':20, 'banana':5, 'rotten tomato': 1}
>>> print(sorted(d.items(), key=lambda x: x[1]))
[('rotten tomato', 1), ('banana', 5), ('apple', 10), ('orange', 20)]


"""Sort using operator.itemgetter as the sort key instead of a lambda"""
>>> from operator import itemgetter
>>>
>>> print(sorted(d.items(), key=itemgetter(1)))
[('rotten tomato', 1), ('banana', 5), ('apple', 10), ('orange', 20)]


"""Sort dict keys by value"""
>>> print(sorted(d, key=d.get))
['rotten tomato', 'banana', 'apple', 'orange']
```

## Dictionary 병합
```python
"""merge dict's"""
>>> d1 = {'a': 1}
>>> d2 = {'b': 2}
>>>
>>> print(**d1, **d2)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'a' is an invalid keyword argument for print()
>>>
>>> print({**d1, **d2})
{'a': 1, 'b': 2}
>>>
>>> print(dict(d1.items() | d2.items()))
{'a': 1, 'b': 2}
>>>
>>> d1.update(d2)
>>> print(d1)
{'a': 1, 'b': 2}
```

## For Loop문에서 Else 활용
```python
"""else gets called when for loop does not reach break statement"""
>>> a = [1, 2, 3, 4, 5]
>>> for element in a:
...     if element == 0:
...             break
... else:
...     print('did not break out of for loop')
...
did not break out of for loop
```
