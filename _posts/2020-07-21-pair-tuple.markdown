---
layout: post
title:  "pair and tuple in C++"
date:   2020-07-21 20:15
categories: ["c++"]
author: "J-Shine"
---

# pair와 tuple
pair는 두개의 값, tuple은 3개 이상의 값을 함께 묶어서 다닐 때 유용한 STL이다.<br>
좌표를 설정할 때 pair 또는 tuple을 사용한다.<br><br>

# pair
```c++
pair<int, int> p1 = make_pair(1, 2); // pair 생성 후 1, 2로 초기화
pair<int, int> p2 = { 1, 2 }; // pair 생성 후 1, 2로 초기화 (C++11 이상)
cout << p1.first << '\n'; // 첫 번째 원소인 1 출력
cout << p1.second << '\n'; // 두 번째 원소인 2 출력
```

# tuple(C++TR1 이상)
```c++
tuple<int, int, int> t1 = make_tuple(1, 2, 3); // tuple 생성 후 1, 2, 3으로 초기화
tuple<int, int, int> t2 = { 1, 2, 3 }; // tuple 생성 후 1, 2, 3으로 초기화
cout << get<0>(t1) << '\n'; // 첫 번째 원소인 1 출력
cout << get<1>(t1) << '\n'; // 두 번째 원소인 2 출력
cout << get<2>(t1) << '\n'; // 두 번째 원소인 3 출력
```
