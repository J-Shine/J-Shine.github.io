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
print("""\                  # \를 붙여주면 개행문자를 문자열에 입력받지 않는다.
Usage: thingy [OPTIONS]
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
# 인접한 문자열
서로 인접한 문자열들은 그냥 합쳐진다.
```
'Python'

# 인덱스 사용

[출처](https://docs.python.org/3/tutorial/)
