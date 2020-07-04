---
layout: post
title:  "[2562번] 최댓값"
date:   2020-07-04 23:30
categories: ["baekjoon-algorithm"]
author: "J-Shine"
---

# max number problem

9개의 서로 다른 자연수가 주어질 때, 이들 중 최댓값을 찾고 그 최댓값이 몇 번째 수인지를 구하는 프로그램을 작성하시오.<br>

예를 들어, 서로 다른 9개의 자연수<br>

3, 29, 38, 12, 57, 74, 40, 85, 61<br>

이 주어지면, 이들 중 최댓값은 85이고, 이 값은 8번째 수이다.<br><br>

# 입력

첫 째 줄부터 아홉 번째 줄까지 한 줄에 하나의 자연수가 주어진다. 주어지는 자연수는 100 보다 작다.<br>

# 출력

첫째 줄에 최댓값을 출력하고, 둘째 줄에 최댓값이 몇 번째 수인지를 출력한다.<br>

```c++
#include<bits/stdc++.h>

using namespace std;

void maxNum(int *numArr) {
	int max = numArr[0];
	int idx = 0;

	for (int i = 1; i < 9; i++) {
		if (max < numArr[i]) {
			max = numArr[i];
			idx = i;
		}
	}
	cout << max << endl;
	cout << idx + 1 << endl;
}

int main() {
	int input = 0;
	int arr[9] = { 0 };
	for (int i = 0; i < 9; i++) {
		cin >> input;
		arr[i] = input;
	}
	maxNum(arr);
	return 0;
}

```
내가 푼 풀이<br>
**배열 넘길 땐 포인터로 넘기기!**<br>
굳이 함수를 만들 필요는 없었지만 그냥 캡슐화 연습했다<br>
