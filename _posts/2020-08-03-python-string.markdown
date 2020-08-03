---
layout: post
title:  "str in python"
date:   2020-08-02 22:00
categories: ["python"]
author: "J-Shine"
---

## **str**
파이썬에서 문자열 자료형은 str이라고 부른다.<br>

## **생성**

**' '또는 " "**를 이용하면 str이 생성되고, 어느 것을 쓰든 상관없다.<br>
' '안에서 '를 쓰고 싶을 땐 \\'라고 쓰면 된다.<br>
' '안에서 "를 쓸 때는 그냥 쓰면 된다.(반대로도 성립)<br>
```python
>>> 'This is J-Shine\'s blog'    # ' '안에서 '를 쓸 땐 \'로 쓴다.
"This is J-Shine's blog"
>>> "This is J-Shine's blog"     # " "안에서 '를 쓸 땐 그냥 '로 쓴다.
"This is J-Shine's blog"
```
<br><br>
**''' ''' 또는 """ """**를 이용하면 여러 줄로 되어있는 문자열을 만들 수 있다.<br>
```python
# 입력
print("""
Usage: thingy [OPTIONS]
    -h
    -H hostname
""")
# 출력
                        
Usage: thingy [OPTIONS]
    -h
    -H hostname

```
이 때 \를 넣어주면 개행문자를 문자열에 입력받지 않는다.<br>
```python
# 입력
print("""\                  
    -h
    -H hostname\
""")
# 출력        
Usage: thingy [OPTIONS]
    -h
    -H hostname
```
<br><br>
## **출력**
print() 함수를 이용하여 출력할 수 있다.<br>
print() 함수 내부에서는 \n이 줄바꿈, \t이 탭 등 특수한 역할을 한다.<br>
만약 \n, \t 등을 문자와 관계없이 print()에서 그냥 쓰고 싶다면 문자열 앞에 raw string을 의미하는 r을 붙이면 된다.<br>
```python
>>> print('C:\some\name')   # print() 함수에선 \n가 개행을 의미한다.
C:\some
ame
>>> print(r'C:\some\name')  # print()함수에서 ' '앞에 r을 붙이면 raw string을 의미해서 \n이 그대로 나온다.
C:\some\name
```
<br>
## **조작**

# +와 \* 사용

+를 이용하면 두 문자열을 합칠 수 있고, \*를 이용하면 문자열을 반복할 수 있다.<br>
```python
>>> 3 * 'un' + 'ium'   # 'un' 3번 반복 후 'ium'
'unununium'
```
변수와도 합칠 수 있다.<br>
```python
# 입력
a = 'Py'
print(a + 'thon')
# 출력
'Python'
```
<br>

# 인접한 문자열
서로 인접한 문자열들은 그냥 합쳐진다.
```python
>>> 'Py' 'thon'
'Python'
```
<br>

# 인덱싱 사용
str은 문자열이므로 인덱스로 접근할 수 있다.<br>
첫 번째 문자는 0번이고, 한 글자 당 한 칸이다.(한글도 마찬가지)<br>
```python
# 입력
a = 'Hello'
print(a[0])
print(a[1])
b = '안녕하세요'
print(b[0])
print(b[1])

# 출력
H
e
안
녕
```
뒤에서 카운트할 수도 있다. -1부터 시작한다.<br>

```python
# 입력
a = 'Hello'
print(a[-1])
print(a[-2])
b = '안녕하세요'
print(b[-1])
print(b[-2])

# 출력
o
l
요
세
```
<br><br>

str 자료형은 immutable 속성이기 때문에 수정이 불가능하다. 수정을 위해서는 새로 만드는게 낫다.<br>
```python
# 입력
a = 'Python'
a[0] = 'J'

# 출력
TypeError                                
Traceback (most recent call last)

      1 a = 'Python'
----> 2 a[0] = 'J'
      3 

TypeError: 'str' object does not support item assignment
```
<br><br>

# 슬라이싱 사용
슬라이싱은 : 를 이용하여 주어진 str의 substr을 반환한다. 문자열 뿐만 아니라 파이썬의 다른 시퀀스형태에서도 사용하는 개념이다.<br>
파이썬에서는 슬라이싱기능을 자주 사용하는데 쓸 때마다 헷갈리기 때문에 제대로 개념을 잡아야 좋다.<br><br>
예를 들어 a\[1:4] 는 a의 1번 인덱스부터 4번인덱스 전까지의 문자열을 반환한다.<br>
```python
>>> a = 'Python'
>>> a[1:4]
'yth'
```
a\[1:4]는 a\[slice(1,4,None)]과 같이 slice()를 호출한다.<br>
이 때 range(start, stop, step)이 사용되기 때문에 끝은 포함되지 않고, step을 지정할 수 있다. 지정하지 않으면 자동으로 None이 들어간다.<br>
start=None이면 0부터 시작, stop=None이면 끝에서 끝남, step=None이면 step이 1인게 default이다.<br>

```
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```
위 그림처럼 각 글자들의 인덱스는 글자의 왼쪽에 위치하고, 마지막에 하나의 인덱스가 더 있다고 생각하면 이해가 더 쉽다.<br>
슬라이싱을 할 경우 start와 stop 인덱스 사이의 글자들이 출력된다고 생각하면 된다.<br>

```python
>>> a = 'Python'
>>> a[0:2]      # 0부터 2 전까지
'Py'
>>> a[:2]       # 0부터 2 전까지
'Py'
>>> a[4:]       # 4부터 끝까지
'on'
>>> a[-2:]      # -2(뒤에서 두 번째 글자)부터 끝까지
'on'
>>> a[:]        # 처음부터 끝까지
'Python'
```





[출처](https://docs.python.org/3/tutorial/)
