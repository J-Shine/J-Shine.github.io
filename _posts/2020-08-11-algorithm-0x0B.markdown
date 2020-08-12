---
layout: post
title: "재귀"
date:   2020-08-11 21:56
categories: ["barkingDog"]
author: "J-Shine"
---

# 바킹독님의 실전알고리즘배우기 11강듣고 요약
[바킹독의 실전 알고리즘 11강 링크](https://blog.encrypted.gg/943)   
 
![image](https://user-images.githubusercontent.com/61873510/89894676-7135da00-dc15-11ea-8c0e-fd2f7a533910.png)<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fq86ZB%2FbtqEP4ozPIt%2FG6ovOzLfHh91EDDqtWEkH1%2Fimg.png)<br><br>

# 재귀
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcDtpsr%2FbtqEP4hOlGv%2FsgiBwTicbJVzgm1YkjWpKk%2Fimg.png)<br>
재귀는 하나의 함수에서 자기자신을 다시 호출해 작업을 수행하는 알고리즘이다.<br><br>

# 절차지향적 사고
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcr4TFs%2FbtqEOOAFFXo%2FawEBTnqkOTrMi4pzkJXRu1%2Fimg.png)<br>
재귀함수를 짤 땐 절차지향적 사고를 반드시 탈피해야 한다.<br><br>

# 귀납적 사고
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcowmE2%2FbtqEOPzz7TO%2FyeLFR5ccsN6Q9gsBXCEtek%2Fimg.png)<br>
재귀함수는 반드시 귀납적 사고로 짜야 한다.<br>
귀납적 사고로 재귀함수를 짤 땐 'func1(1)이 1을 출력한다.'와 'func1(k)가 k, k-1, ... , 1을 출력하면 func1(k+1)은 k+1, k, ..., 1을 출력한다.'만 성립시키면 된다.<br><br>

# 재귀함수의 조건
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbvspRF%2FbtqENZiCNVb%2FKwu0ixB2aL1aAmWAr0FKPk%2Fimg.png)<br>
재귀함수에서는 반드시 특정 입력에 대해서는 자기 자신을 호출하지 않고 종료되어야 한다.(base condition)<br>
또한 **모든 입력은 base condition으로 수렴**해야 한다.<br><br>

# 재귀함수에 대한 정보
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Flm5gG%2FbtqEP4ITBlr%2F7qMbW1vj3zwDL7XmUxUxu0%2Fimg.png)<br>
재귀함수를 사용하면 코드가 간결해지지만 함수 호출이 비용이 큰 연산이기 때문에 메모리와 시간에서 손해를 본다.<br>
재귀함수말고 반복문을 사용하면 빠르게 동작할 수 있지만 코드가 너무 복잡해질 수 있다.<br>
따라서 재귀를 쓰지 않아도 구현에 큰 어려움이 없으면 반복문으로 짜면 좋고, 코드가 복잡한 일부 문제들은 재귀를 쓰는게 좋다.<br>
어떨 때 재귀를 쓰고 어떨 때 재귀가 필요없는지는 많은 문제를 풀고 경험해보아야 한다.<br><br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FlTnv6%2FbtqEPuadETu%2FLivDGzlCp922Ldhp3T7kGK%2Fimg.png)<br>
자기 자신을 한번에 두 개 이상 호출하는 재귀함수는 위 그림처럼 비효율적일 수 있다.<br><br>

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FNgNyr%2FbtqENZJFsaV%2FhTDYcaKCzVztqznPRSBqBK%2Fimg.png)<br>
지역변수는 스택 영역에 쌓이므로 재귀함수가 자기 자신을 부를 때 스택 영역에 계속 누적되어 메모리를 잡아먹는다.<br>
swexpertacademy처럼 스택 메모리에 1MB 제한이 걸려있는 경우에는 스택에 많이 쌓이는 재귀 대신 반복문으로 문제를 풀어야 한다.<br><br>


# 재귀 연습 문제 1 - 거듭제곱 1
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbZYABP%2FbtqEPmXMo1U%2FfjTBKRn2m6KDJtfBZ9oIx0%2Fimg.png)<br>
a^b mod m을 구할 때 a^b를 구하고 거기에 m을 나누면 a^b의 숫자가 너무 커져서 overflow가 난다.<br>
따라서 a^b를 모두 구한 후 m을 나누기보단 a * a에 % m을 매번 해주는게 좋다. 그렇게 되면 a가 2^32보다 작다고 할 때 long long에서 overflow가 발생하지 않고 O(b)에 답을 구할 수 있다.<br><br>

# 재귀 연습 문제 1 - 거듭제곱 2
백준 1629번: 곱셈<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0s3zd%2FbtqEOaxqSM5%2FbBXxKzLUW6dcmKSVbJWHDK%2Fimg.png)<br>
1승을 base condition으로 하고, k승을 계산하고 2k와 2k+1을 계산할수 있다는 것을 이용하여 푼다.<br>
나는 이걸 보고서도 어떻게 풀지 몰라서 결국 답봤다. 그래서 풀지도 못했는데 바킹독님 코드로 따로 포스팅하기도 노양심같아서 그냥 여기다가 씀.<br>

아래는 바킹독님 풀이
```c++
// http://boj.kr/a9f89b45ac624c2a8d13f27a01dd78d1
#include <bits/stdc++.h>
using namespace std;

using ll = long long;

ll POW(ll a, ll b, ll m){
  if(b==1) return a % m;
  ll val = POW(a, b/2, m);
  val = val * val % m;
  if(b%2 == 0) return val;
  return val * a % m;
}

int main(void){
  ios::sync_with_stdio(0);
  cin.tie(0);
  ll a,b,c;
  cin >> a >> b >> c;
  cout << POW(a,b,c);
}
```
앞에서 2k와 2k + 1을 이용한다고 했지만, **결국 base condition으로 수렴하게 만들어야 하므로** 작은 수에 2를 곱하는 대신 큰 수에서 2를 나누는 방식으로 구현한다.<br>
2를 나눌 때 2k와 2k + 1일 때의 몫이 같게 나오므로 짝수일 때와 홀수일 때를 나누어서 구현해준다.<br>
이 함수의 시간복잡도는 b가 계속 절반씩 깎이기 때문에 O(logb)이다.<br><br>

# 재귀 연습 문제 2 - 하노이 탑
백준 11729번: 하노이 탑 이동 순서<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcq0ig0%2FbtqENYYmp3g%2FSIRh1KMgfXup6gmh7lPlV1%2Fimg.png)<br>
n개의 원판을 옮기는 법은 위와 같이 3단계로 나누어 생각할 수 있다.<br>
n개의 원판을 옮길 수 있으면 n-1개의 원판도 옮길 수 있으므로 결국 f(n)을 f(n-1)로 표현 하면 된다.<br>
이를 구체화하기 위해선 아래처럼 함수의 정의 base condition, 재귀 식을 생각해준다.<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FvrZfm%2FbtqEOaqORJL%2F3sFJWQ4KxakszOpavndg10%2Fimg.png)<br>
아래는 바킹독님 풀이<br>
```c++
// http://boj.kr/f2440915dca04aaa9aec759080516973
#include <bits/stdc++.h>
using namespace std;

void func(int a, int b, int n){
  if(n == 1){
    cout << a << ' ' << b << '\n';
    return;
  }
  func(a, 6-a-b, n-1);
  cout << a << ' ' << b << '\n';
  func(6-a-b, b, n-1);
}

int main(void){
  ios::sync_with_stdio(0);
  cin.tie(0);
  int k;
  cin >> k;
  cout << (1<<k) - 1 << '\n';
  func(1, 3, k);
}
```
func 함수가 n개의 원판을 1번에서 3번으로 모두 옮기는 함수라고 생각하면
함수 내부의 동작은 n-1개의 원판을 2번으로 옮기기 위해 func(n-1)을 부르고, n을 3번으로 옮기고, n-1개의 원판을 3번으로 옮기기 위해 func(n-1)을 다시 부른다.<br>
이 때 1번에서 2번, 2번에서 3번 가는 동작은 구별해줘야 하므로 시작 지점과 출발지점을 인자로 함께 받는다.<br>
그리고 main 함수에서 1<<k라는 코드가 있는데 이 때 <<는 left shift라는 비트연산자로, 1<<k는 1을 비트 기준으로 k칸 왼쪽으로 밀어 라는 뜻이기 때문에 1<<k는 2^k가 된다.<br><br>


# 재귀 연습 문제 3 - Z
백준 1074번: Z<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FFvrpn%2FbtqEPVTpmD1%2FIaGruhm4vyZCrRhQFtYwMK%2Fimg.png)<br>
위 그림처럼 큰 변이 2^n일 때 1234 네개로 나눈 작은 사각형의 변은 2^(n-1)이다.<br>
이 때 2번째 작은 사각형은 첫번째 작은 사각형을 모두 돌고나서 시작되고,<br>
3번째 작은 사각형은 첫번째와 두번째 작은 사각형을 모두 돌고나서 시작되므로 앞의 사각형 값을 모두 더해주고 나서 func(n-1)을 다시 부르는 방식으로 재귀함수를 만든다.<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fr315x%2FbtqEPgxcyOL%2Fz3AKdgjKKcczoPaFjgoB61%2Fimg.png)<br>
따라서 위 슬라이드처럼 재귀식이 나온다.<br>
아래는 바킹독님 풀이<br>
```c++
#include <bits/stdc++.h>
using namespace std;

int func(int n, int r, int c){
  if(n == 0) return 0;
  int half = 1<<(n-1);
  if(r < half && c < half) return func(n-1, r, c);
  if(r < half && c >= half) return half*half + func(n-1, r, c-half);
  if(r >= half && c < half) return 2*half*half + func(n-1, r-half, c);
  return 3*half*half + func(n-1, r-half, c-half);
}

int main(void){
  ios::sync_with_stdio(0);
  cin.tie(0);
  int n, r, c;
  cin >> n >> r >> c;
  cout << func(n, r, c);
}
```
끗

