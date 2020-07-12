---
layout: post
title:  "Pointer(*) vs Reference(&) "
date:   2020-07-07 19:50
categories: ["c++"]
author: "J-Shine"
---

# C/C++에서 pointer(*)와 reference(&)의 차이점
[Pointers vs References in C++ 정리 링크](https://www.geeksforgeeks.org/pointers-vs-references-cpp/)   
  
  
# 포인터와 참조자의 정의
포인터는 다른 변수의 주소를 저장하는 변수이다.<br>
참조자는 이미 존재하는 변수에게 새로운 이름을 주는 것이다.<br><br>
# 변수 초기화
포인터는 선언만 하고 초기화 하지 않을 수도 있다.<br>
참조자는 선언과 함께 초기화까지 해주어야 한다.<br><br>

# 값 재할당
포인터는 변수의 값을 재할당 할 수 있다.<br>
참조자는 변수의 값을 재할당 할 수 없다.<br><br>
# NULL 값
포인터는 NULL 값을 가리킬 수 있다.<br>
참조자는 NULL 값을 가리킬 수 없다.<br><br>
# 다중 연산
포인터는 이중, 삼중 등 다중 포인터를 가질 수 있다.<br>
참조자는 다중 연산이 불가능하다. 참조자를 참조자로 참조할 수 없다.<br><br>
