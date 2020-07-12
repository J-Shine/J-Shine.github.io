---
layout: post
title:  "Pointer/Array/String in C/C++"
date:   2020-07-08 19:20
categories: ["c++"]
author: "J-Shine"
---

# 배열과 포인터
## 배열은 포인터와 조금 유사한 면이 있다.
배열과 포인터는 모두 '주소'를 나타낸다.<br>
배열과 포인터 모두 '*' 연산과 '[]' 연산이 가능하다.<br>

```c++
int arr[] = { 5, 10, 15 };
int* parr = arr;
// 5 5 5 5 를 출력
cout << arr[0] << ' ' << *arr << ' ' << parr[0] << ' ' << *parr << "\n";
``` 
## 배열과 포인터의 차이점
arr에 다른값을 넣을 수 없다.
arr == &arr == &arr[0]이다.
```c++
int arr[] = { 5, 10, 15 };
cout << arr << ' ' << &arr << ' ' << &arr[0] << "\n"; // 모두 같은 주소값을 출력
```
## 배열과 포인터는 sizeof() 연산 결과가 다르다.
```c++
int arr[] = { 5, 10, 15 };
int* parr = arr;
cout << "sizeof(arr): " << sizeof(arr) << "\n"; // 12(배열 전체의 메모리 크기)
cout << "sizeof(parr): " << sizeof(parr) << "\n"; // 4(포인터 변수의 메모리 크기)
```

## 포인터의 증가/감소 연산과 배열의 [] 연산
포인터와 배열 모두에서 arr[i] == *(arr+i) 성립
```c++
int arr[] = { 5, 10, 15 };
cout << arr[1] << ' ' << *(arr+1) << "\n"; // 10 10 출력
```

## 함수의 인자로 배열을 전달하는 방법
포인터로 배열의 시작 주소를 전달한다.
배열의 길이도 함께 인자로 전달한다.
**배열을 함수의 인자로 전달할 땐 call-by-value(값전달)가 아닌 call-by-reference(주소전달)를 해야 한다.**
```c++
void passArray(int* arr, int len) {
	for (int i = 0; i < len; i++) {
		cout << arr[i] << ' ';
	}
}
```

# 문자열과 포인터
## char* 를 이용하여 문자열을 저장한다.
[참조](http://www.cplusplus.com/forum/general/59834/)   

C에서는 char* 를 이용하여 string(문자열)을 저장한다.<br>
따라서 char 변수에 문자를 저장하고 char* 로 출력해도 주소가 출력되지 않고 문자열이 출력된다.<br>
그런데 문자열을 char 배열로 저장할 때 항상 끝의 칸에 문자열의 끝을 알려주는 \0가 있어야 하는데 없으므로 이상한 쓰레기값이 출력된다.<br><br>

```c++
char* str = "some string"; // this is valid
int* i = 1234; // this not...
// you must allocate memory for the int* like so
int* j = new int;
*j = 1234;

std::cout << str; // prints the string, not the memory address of the pointer
std::cout << j; // prints the memory address of the pointer 
```
## 문자열을 선언하는 두 가지 방법
1. 변수 형태의 문자열<br>
-> 배열의 각 요소에 접근해서 문자열을 수정 가능하다.<br>
```c++
char str1[] = "Some string";
```

2. 상수 형태의 문자열<br>
-> 리터럴로 메모리에 자동 할당된 문자열을 가리키는 **포인터**로, 문자열의 내용을 수정 불가능하다.<br>
```c++
char str2 = "Some other string";
```
