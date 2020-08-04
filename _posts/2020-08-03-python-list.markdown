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
>>> list([1, 2, 3])
[1, 2, 3]
```
<br>
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
>>> a = list((1, 2, 3))
>>> a.append(4)
[1, 2, 3, 4]
>>> a[len(a):] = [5]
[1, 2, 3, 4, 5]
```

**list.extend(iterable)**<br>
list의 끝에 iterable한 객체의 원소들을 차례로 추가한다. a[len(a):] = iterable과 같다.<br>
```python
>>> a = list([1, 2, 3])
>>> a.extend([4, 5])
[1, 2, 3, 4, 5]
```
**list.insert(i, x)**<br>
i는 list의 index, x는 삽입할 객체이다.<br>
i 자리에 x 객체를 삽입한다.<br>
```python
>>> a = list([1, 2, 3])
>>> a.insert(1, [4, 5])
>>> a
[1, [4, 5], 2, 3]
```
**list.remove(x)**<br>
list를 0부터 차례로 훑어가며 가장 처음 만나는 x를 삭제한다.<br>
list에 x가 존재하지 않을 경우 ValueError가 발생한다.<br>
```python
>>> a = [1, [4, 5], 2, 3]
>>> a.remove(2)
>>> a
[1, [4, 5], 3]
```
**list.pop(i)**<br>
i번째에 있는 원소를 삭제하고 반환한다.<br>
index를 지정하지 않을 경우 가장 끝의 원소를 삭제하고 반환한다.<br>
```python
>>> a = [1, [4, 5], 2, 3]
>>> a.pop()
3
>>> a
[1, [4, 5], 2]
>>> a.pop(1)
[4, 5]
>>> a
[1, 2]
```
**list.clear()**<Br>
list의 모든 원소를 제거한다. a\[:]와 같다.<br>
```python
>>> a = [1, [4, 5], 2, 3]
>>> a.clear()
>>> a
[]
>>> a = [1, [4, 5], 2, 3]
>>> a[:] = []
>>> a
[]
```

**list.index(x, start, end)**<br>
list를 처음부터 끝까지 훑으면서 가장 처음 만나는 x의 index를 반환한다.<br>
start나 end를 설정할 경우 슬라이싱처럼 탐색 범위를 제한한다.<br>
```python
>>> a = [2, 3, 1, 1, 1]
>>> a.index(1, 3, 5)    # 3~4에 있는 index 중 처음 만나는 1의 index 반환
3
```
**list.count(x)**<br>
list에 x가 몇 개 있는지 반환한다.<br>
```python
>>> a = [2, 3, 1, 1, 1]
>>> a.count(1)
3
```
**list.sort(key=None, reverse=False)**<br>
list를 정렬한다.<br>
Parameter<br>
    key - 정렬하는 기준을 정한다. default=None(첫 원소부터 차례대로)<br>
    reverse - True일 땐 내림차순, False일 땐 오름차순이다. default=False<br>
```python
# 입력
l = [
    ['john', 'A', 15],
    ['jane', 'B', 12],
    ['dave', 'B', 10],
    ['dave', 'A', 10]
]
l.sort()
print(l)

# 출력
[['dave', 'A', 10], ['dave', 'B', 10], ['jane', 'B', 12], ['john', 'A', 15]]
```
operator 모듈의 itemgetter(), attrgetter(), methodcaller()를 이용하면 key를 사용하기 편리하다.<br>
```python
# 입력
from operator import itemgetter
l = [
    ['john', 'A', 15],
    ['jane', 'B', 12],
    ['dave', 'B', 10],
    ['dave', 'A', 10]
]
l.sort(key=itemgetter(2,1))        # 3번째 열 기준으로 배열, 만약 같으면 2번째 열이 다음 기준
print(l)

# 출력
[['dave', 'A', 10], ['dave', 'B', 10], ['jane', 'B', 12], ['john', 'A', 15]]
```
```python
# 입력
class Student:
    def __init__(self, name, grade, age):
        self.name = name
        self.grade = grade
        self.age = age
    def __repr__(self):
        return repr([self.name, self.grade, self.age])
student_objects = [
    Student('john', 'A', 15),
    Student('jane', 'B', 12),
    Student('sam', 'B', 10),
    Student('dave', 'B', 10)
]
student_objects.sort(key=attrgetter('age','name'))  # age를 첫 번째 기준, name을 두 번째 기준으로 정렬.
print(student_objects)

# 출력
[['dave', 'B', 10], ['sam', 'B', 10], ['jane', 'B', 12], ['john', 'A', 15]]

```

**list.reverse()**<br>
list 원소들의 위치를 정반대로 만든다.<br>
```python
>>> l = [1, 5, 3, 8, 4]
>>> l.reverse()
>>> l
[4, 8, 3, 5, 1]
```

**list.copy()**<br>
list의 shallow copy를 반환한다.<br>
a\[:]와 같다.<br>
```python
>>> l = [1, 5, 3, 8, 4]
>>> l2= l.copy()
>>> l2
[1, 5, 3, 8, 4]
```





[출처](https://docs.python.org/3/tutorial/)
[출처](https://docs.python.org/3/library/)
