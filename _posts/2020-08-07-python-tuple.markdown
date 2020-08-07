---
layout: post
title:  "tuple in python"
date:   2020-08-07 22:00
categories: ["python"]
author: "J-Shine"
---

## **tuple**
파이썬에서 tuple은 여러가지 자료형의 객체를 차례로 담을 수 있다.<br>
[list](https://j-shine.github.io/python/2020/08/03/python-list.html)자료형과 거의 같은데, 차이점은 list는 mutable, tuple은 immutable하다는 것이다.<br>
또한 일반적으로 서로 이질적인 자료형을 담을 때 tuple이 list보다 더 자주 사용된다.<br>

## **생성**
**()**와 **,**를 이용하면 tuple을 만들 수 있다. 이 때 중요한 것은 ()가 아니라 **,**이다.<br>
()는 문법상의 모호함을 피하고자 할 때만 필수로 사용한다.<br>

```python
>>> t = 12345, 54321, 'hello!'  # ,를 이용하여 tuple 만들기
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> u = t, (1, 2, 3, 4, 5)      # 다른 tuple 속에 tuple 넣기
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
>>> ()                          # 빈 tuple 만들기
()
>>> singleton = 'hello',        # 원소가 하나인 tuple 만들기
>>> len(singleton)
1
>>> singleton
('hello',)
```
tuple() 함수 이용<br>
```python
>>> tuple((1,))
(1,)
```
<br><br>
## **조작**
tuple은 immutable 객체이므로 원소를 읽어들이는 것 위주의 조작이 가능하다.<br>
즉 [공통시퀀스]() 연산과 hash()가 가능하다.<br>

# 인덱싱과 슬라이싱 이용
```python
>>> tp = 1, 2, 3, 4, 5
>>> tp[0]   # 0번 인덱스 반환
1
>>> tp[2:4] # 2번부터 4번 전까지 슬라이싱
(3, 4)
>>> tp[0::2] # 0번부터 끝까지 step=2로 슬라이싱
(1, 3, 5)
```
<br><br>

# **\***와 **+** 이용 
immutable한 자료형이라 원소 수정은 불가능하지만 *나 +를 이용한 이어붙이기는 가능하다.<br>

```python
>>> tp1 = 1, 2, 3, 4, 5
>>> tp2 = 6, 7
>>> tp1 + tp2
(1, 2, 3, 4, 5, 6, 7)
>>> tp1 * 3
(1, 2, 3, 4, 5, 1, 2, 3, 4, 5, 1, 2, 3, 4, 5)
```
<br><br>

# 함수 이용

**tuple.index(x, start, end)**<br>
tuple을 처음부터 끝까지 훑으면서 가장 처음 만나는 x의 index를 반환한다.<br>
start나 end를 설정할 경우 슬라이싱처럼 탐색 범위를 제한한다.<br>
```python
>>> a = (2, 3, 1, 1, 1)
>>> a.index(1, 3, 5)    # 3~4에 있는 index 중 처음 만나는 1의 index 반환
3
```
**tuple.count(x)**<br>
tuple에 x가 몇 개 있는지 반환한다.<br>
```python
>>> a = (2, 3, 1, 1, 1)
>>> a.count(1)
3
```



[출처](https://docs.python.org/3/tutorial/)
[출처](https://docs.python.org/3/library/)
