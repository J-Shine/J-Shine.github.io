---
layout: post
title:  "list in python"
date:   2020-08-03 22:00
categories: ["python"]
author: "J-Shine"
---

## **list**
파이썬에서 list는 여러가지 자료형의 객체를 차례로 담을 수 있다.<br>

## **생성**

**[]**를 이용하면 list가 생성된다. 각 객체들은 ,로 구분한다.<br>

```python
>>> a = [1, 4, 9, 16, 25]
>>> a
[1, 4, 9, 16, 25]
```
<br>

반드시 하나의 자료형으로 통일할 필요가 없고, 서로 달라도 된다.<br>
```python
# 입력
a = [1, 1.23, 'Python', True] # 여러가지 데이터 타입으로 list 생성
for data in a:            # list의 데이터 타입을 차례로 출력
    print(type(data))

# 출력
<class 'int'>
<class 'float'>
<class 'str'>
<class 'bool'>
```

내용물을 넣지 않으면 빈 list 객체가 생성된다.<br>
```python
>>> a = []
>>> type(a)
list

>>> a[0]
IndexError                                
Traceback (most recent call last)
----> 1 a[0]

IndexError: list index out of range
```
<br><br>

list 안에 list를 넣을 수도 있다.<br>





## **조작**

# 인덱싱과 슬라이싱 이용
list는 mutable 객체이므로 인덱싱과 슬라이싱으로 원소를 변경할 수 있다.<br>
```python
# 입력
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g'] # list 생성
print(letters)
letters[2:5] = ['C','D','E'] # 슬라이싱으로 c, d, e를 대문자로 바꿈
print(letters)
letters[2:5] = [] # 슬라이싱으로 C, D, E를 제거
print(letters)
letters[:] = [] # 슬라이싱으로 모든 원소 제거
print(letters)

# 출력
['a', 'b', 'c', 'd', 'e', 'f', 'g']
['a', 'b', 'C', 'D', 'E', 'f', 'g']
['a', 'b', 'f', 'g']
[]
```
<br><br>

# 함수 이용











[출처](https://docs.python.org/3/tutorial/)
