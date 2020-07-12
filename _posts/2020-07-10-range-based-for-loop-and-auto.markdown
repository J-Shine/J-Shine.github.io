---
layout: post
title: "Range-based for loop and Auto"
date: 2020-07-10 15:06
categories: ["etc"]
author: "J-Shine"
---

# Range-based for loop(C++11 이상에서 지원)
```c++
#include <bits/stdc++.h>
using namespace std;
int main() {
	int arr[] = { 1, 2, 3, 4, 5 };
	for (auto e : arr) {
		cout << "e: " << e << " ";
	}
}
```
## 범위 기반 for문이 기존 for문과 다른 점
1. 범위 기반 for문은 *배열과 vector 등 순회가 가능한 데이터타입*을 *처음부터 끝까지* 순회하는 연산을 한다.<br>
-> 섬세한 조절이 힘들다.<br>
2. 범위 기반 for문은 순회할 때 element에 배열의 값을 복사한다(deep copy).<br>
-> O(N)의 시간복잡도를 가진다.<br><br>

## reference(&) 사용
reference(&)를 사용하면 deep copy를 피할 수 있다. -> 시간복잡도 O(1)<br><br>

## auto
auto는 타입추론변수이다.<br>
변수 생성과 함께 초기화를 해주어야 그것을 바탕으로 타입을 추론한다.<br><br>
