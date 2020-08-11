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
지역변수는 스택 영역에 쌓이므로 재귀함수가 자기 자신을 부를 때 스택 영역에 계속 누적되어 메모리를 잡아먹는다.<br><br>

