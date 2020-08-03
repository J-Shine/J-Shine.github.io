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
<br><br>
**[]**를 이용하면 list가 생성된다. 각 객체들은 ,로 구분한다.<br>

```python
>>> a = [1, 4, 9, 16, 25]
>>> a
[1, 4, 9, 16, 25]
```

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

list 안에 list를 넣을 수도 있다.<br>
```python
# 입력
x = [['a', 'b', 'c'], [1, 2, 3]]
print(x[1])
print(x[1][1])

#출력
[1, 2, 3]
2
```
<br>
**list()** 생성자를 이용하여 list를 생성할 수도 있다.<br>
인자는 iterable이다.<br>
```python
>>> list()
[]
>>> list([1, 2, 3]
[1, 2, 3]
```
**for문**을 이용하여 list를 생성할 수도 있다.<br>
\[x for y in iterable] 형태로 사용 <br>
iterable한 객체를 순서대로 y라고 했을 때 그 자리에 x를 넣는다.<br>
```python
# 입력
a = [1, 1.23, 'Python', True]
x = [['a', 'b', 'c'], [1, 2, 3]]
b = [a for i in x[0]]
print(b)
print(type(b[0]))

# 출력
[[1, 1.23, 'Python', True], [1, 1.23, 'Python', True], [1, 1.23, 'Python', True]]
<class 'list'>
```

<br><br>

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
**list.append(x)**<br>
list의 끝에 객체 x를 저장한다. a\[len(a):] = \[x]와 같다.<br>
```python
>>> a = list([1, 2, 3])
>>> a.append(4)
[1, 2, 3, 4]
```

list.extend(iterable)
Extend the list by appending all the items from the iterable. Equivalent to a[len(a):] = iterable.

list.insert(i, x)
Insert an item at a given position. The first argument is the index of the element before which to insert, so a.insert(0, x) inserts at the front of the list, and a.insert(len(a), x) is equivalent to a.append(x).

list.remove(x)
Remove the first item from the list whose value is equal to x. It raises a ValueError if there is no such item.

list.pop([i])
Remove the item at the given position in the list, and return it. If no index is specified, a.pop() removes and returns the last item in the list. (The square brackets around the i in the method signature denote that the parameter is optional, not that you should type square brackets at that position. You will see this notation frequently in the Python Library Reference.)

list.clear()
Remove all items from the list. Equivalent to del a[:].

list.index(x[, start[, end]])
Return zero-based index in the list of the first item whose value is equal to x. Raises a ValueError if there is no such item.

The optional arguments start and end are interpreted as in the slice notation and are used to limit the search to a particular subsequence of the list. The returned index is computed relative to the beginning of the full sequence rather than the start argument.

list.count(x)
Return the number of times x appears in the list.

list.sort(key=None, reverse=False)
Sort the items of the list in place (the arguments can be used for sort customization, see sorted() for their explanation).

list.reverse()
Reverse the elements of the list in place.

list.copy()
Return a shallow copy of the list. Equivalent to a[:].










[출처](https://docs.python.org/3/tutorial/)
[출처](https://docs.python.org/3/library/)
