---
layout: post
title: "백트래킹"
date:   2020-08-28 19:35
categories: ["barkingDog"]
author: "J-Shine"
---

# 바킹독님의 실전알고리즘배우기 12강듣고 요약
[바킹독의 실전 알고리즘 12강 링크](https://blog.encrypted.gg/945)   
 
 
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FOaYTM%2FbtqFnZgHMXI%2FIXMJLTVyJiJJjkKpbbzhu1%2Fimg.png)<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fln91p%2FbtqFoQJ8g3J%2FM8AKkJCOD6CLBXOQtvJaw0%2Fimg.png)<br><br>

# 백트래킹
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FzMPI9%2FbtqFlj12wS5%2F44iU3WIEfCGsFL60362C0k%2Fimg.png)<br>
백트래킹은 현재 상태에서 가능한 모든 후보군을 따라 들어가며 탐색하는 알고리즘이다.<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FZixlJ%2FbtqFo5BSuI6%2FgqouLzEcynH3RXErPv2Om1%2Fimg.png)<br>
위 그림처럼 모든 경우의 수를 따지는데, 끝에 도달했다가 다시 이전의 분기점으로 돌아와서 다른 경우의 수로 가는 형식이라서 DFS와 비슷하고, DFS보다는 좀 더 넓은 개념으로 쓰인다.<br>
<br>
[출처](https://stackoverflow.com/questions/1294720/whats-the-difference-between-backtracking-and-depth-first-search)<br><br>

# 백트래킹 연습 문제 1 - N과 M(1)
백준 15649번: N과 M(1)[링크](https://www.acmicpc.net/problem/15649)<br>
1부터 N까지의 자연수 중에서 중복 없이 M개를 고른 수열을 구하는 문제이다.<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbFQg5D%2FbtqFmuIYVJb%2Fo2ilY8jSBYMyHgRH1bhLhk%2Fimg.png)<br>
위 슬라이드는 N이 4, M이 3일 때의 예시이다. 노란 별은 현재 있는 state를 나타낸다<br>
처음에 빈 배열에서 시작하여 1부터 차례로 집어넣으며 상태공간트리를 만든다.<br>
1, 2, 3을 차례로 넣어 첫 번째 수열을 만들고, 1, 2를 넣었던 상태로 되돌아가서 이번에는 3 대신 4를 넣는다.<br>
그 다음에는 1, 2 다음에 넣어야 할 숫자를 다 넣었으므로 하나 더 뒤의 상태(1만 넣은 상태)로 되돌아가서 이번에는 1 뒤에 3을 넣는다.<br>
같은 방식으로 모든 수열을 찾을 때까지 반복한다.<br>
아래는 구현한 코드<br>
```c++
// http://boj.kr/f36567ec0c9f44b4b460b5b29683c27b
#include <bits/stdc++.h>
using namespace std;

int n,m;
int arr[10];
bool isused[10];

void func(int k){ // 현재 k개까지 수를 택했음.
  if(k == m){ // m개를 모두 택했으면
    for(int i = 0; i < m; i++)
      cout << arr[i] << ' '; // arr에 기록해둔 수를 출력
    cout << '\n';
    return;
  }

  for(int i = 1; i <= n; i++){ // 1부터 n까지의 수에 대해
    if(!isused[i]){ // 아직 i가 사용되지 않았으면
      arr[k] = i; // k번째 수를 i로 정함
      isused[i] = 1; // i를 사용되었다고 표시
      func(k+1); // 다음 수를 정하러 한 단계 더 들어감
      isused[i] = 0; // k번째 수를 i로 정한 모든 경우에 대해 다 확인했으니 i를 이제 사용되지않았다고 명시함.
    }
  }
}

int main(void){
  ios::sync_with_stdio(0);
  cin.tie(0);
  cin >> n >> m;
  func(0);
}
```
백트래킹을 구현하기 위해 isused[10]라는 배열을 만들어서 숫자가 앞에서 사용되었는지 아닌지를 체크한다.<br>
사용이 안 된 숫자라면 isused를 true로 만들고, 사용하고, 함수를 다시 불러서 다음 단계로 간다.<br>
func함수 밑의 줄은 이미 func을 다 실행하고 온 상태이므로 isused를 false로 만들어 원래 상태로 만든다.<br><br>


# 백트래킹 연습 문제 2 - N-Queen
백준 9663번: N-Queen[링크](https://www.acmicpc.net/problem/9663)<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcgt6PF%2FbtqFnFiJQby%2FdaALMfK6nMO9KXqY2sfA11%2Fimg.png)<br>
N X N의 체스판에 N개의 퀸을 서로 공격하지 못하는 위치에 놓는 경우의 수를 구하는 문제이다.<br>
이를 푸는 일반적인 방법은 1행의 1열부터 차례로 행을 내려가면서 퀸들이 서로 공격하지 못하게 배치해보는 것이다.<br>
이를 백트래킹으로 구현할 수 있는데, 현재 어떤 행에 있는지 나타내주는 int cur를 0으로 시작하여 잡고 다음 행에 배치되는 퀸이 위의 퀸들과 위, 대각선으로 겹치지 않게 한다.<br>
그런데 이와 같은 방법은 매 번 위와 겹치지 않는지 계산하여 확인해야하는 오버헤드가 있으므로 배열을 새로 만들어 놓지 못하는 칸을 지워나가는 식으로 해주면 더 빠르다.<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbaqCMt%2FbtqFogvVs7t%2FdtT2VwKE3PUy4Y06WLOql0%2Fimg.png)<br>
위 슬라이드와 같이 isused 배열을 3개를 만든다.<br>
하나는 퀸의 열이 겹치지 않는지 확인하는 용도이고 두 번째는 오른쪽위 대각선, 세 번째는 왼쪽 위 대각선을 확인한다.<br>
바킹독님 코드는 아래와 같다.<br>
```c++
// http://boj.kr/4e7fe4509a3842598592fe4ed79900c0
#include <bits/stdc++.h>
using namespace std;
bool isused1[40]; // column을 차지하고 있는지
bool isused2[40]; // / 방향 대각선을 차지하고 있는지
bool isused3[40]; // \ 방향 대각선을 차지하고 있는지

int cnt = 0;
int n;
void func(int cur) { // cur번째 row에 말을 배치할 예정임
  if (cur == n) { // N개를 놓는데 성공했다면
    cnt++;
    return;
  }
  for (int i = 0; i < n; i++) { // (cur, i)에 퀸을 놓을 예정
    if (isused1[i] || isused2[i+cur] || isused3[cur-i+n-1]) // column이나 대각선 중에 문제가 있다면
      continue;
    isused1[i] = 1;
    isused2[i+cur] = 1;
    isused3[cur-i+n-1] = 1;
    func(cur+1);
    isused1[i] = 0;
    isused2[i+cur] = 0;
    isused3[cur-i+n-1] = 0;
  }
}
int main(void) {
  ios::sync_with_stdio(0);
  cin.tie(0);
  cin >> n;
  func(0);
  cout << cnt;
}
```
이 때 함수에서 빠져나오면서 다시 isused를 false로 바꿔주는 것을 까먹으면 안된다.<br>
위와 같이 A1에 퀸을 놓으면 바로 B1, B2에 퀸을 놓는 경우를 해볼 필요가 없어 지는 것을 백트래킹에서 가지치기라고 부른다<br>
이 가지치기가 빈번하면 시간복잡도가 잘 가늠이 안간다.<br>
만약 N이 많이 작아서 백트래킹으로 푸는 문제일 것 같다는 생각이 들면 직접 구현한 뒤 가장 오래걸릴만한 케이스를 찾아서 시간초과가 나는지를 보면 된다.<br>
시간을 로컬에서 측정할 때는 반드시 release모드로 실행을 해야하고, 보통은 서버가 로컬보다 빠르다는 점을 기억하면 좋다.<br>
Release 모드: 빌드 -> 구성관리자 -> 구성 에서 변경<br>



# 백트래킹 연습 문제 3 - 부분수열의 합
백준 1182번: 부분수열의 합[링크](https://www.acmicpc.net/problem/1182)<br>
N개의 정수로 이루어진 수열의 부분수열 중에서 그 수열의 원소를 다 더한 값이 S가 되는 경우의 수를 구하는 문제이다.<br>
(부분수열: 주어진 수열의 일부 항을 원래 순서대로 나열하여 얻을 수 있는 수열)<br>
한 개의 항이 부분수열에 포함되는지 안되는지의 경우의 수가 2개이므로 n개의 항을 갖는 수열에서 부분수열의 개수는 2^n개이고 공집합을 제외하면 2^n-1개이다.<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FxS0qE%2FbtqFpLXy5Er%2FNJa6250h1O1Zjz723jg7I0%2Fimg.png)<br>
경우의 수를 모두 따지면 위 슬라이드와 같이 상태공간트리를 그릴 수 있고 이를 백트래킹으로 구현하면 된다.<br>
아래는 코드<br>
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbqlJbi%2FbtqFpAorkPW%2FsfdPqow7K7kDrGEarPxZjk%2Fimg.png)<br>
부분수열의 합을 구해야 하므로 함수의 인자로 현재까지의 합을 전달하고, 공집합은 제외하므로 마지막에 cnt--;을 해준다.<br><br> 

# STL next_permutation() 사용하기
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdBgwbm%2FbtqFqLQjXGs%2FAO65dVU4NjBmm75iBDdx20%2Fimg.png)<br>)
next_permutation()은 다음 순열을 구해주는 STL이다.<br>
인자로 받은 순열을 다음 순열로 전환시키고, true를 반환한다. 만약 다음 순열이 없다면 false를 반환한다.<br>
따라서 next_permutation()을 사용할 땐 do-while문을 이용하면 깔끔하다.<br><br>
이 함수로 조합도 구할 수 있는데, 5개에서 3개를 뽑는 조합의 경우 0, 0, 0, 1, 1로 배열을 두고 돌리면 된다.<br>
이 때, 위 슬라이드와 같이 뽑는 수를 0으로 두어 배열의 앞에 먼저 넣고, 안 뽑는 수를 1로 두어 배열의 뒤쪽에 넣는 것이 좀 더 구현하는 데에 편하고 깔끔하다.<br>
단, next_permutation은 항상 쓸 수 있는 것이 아니고, 같은 수를 여러 번 쓸 수 있는 상황에서는 적절하지 않으므로 백트래킹도 잘 익혀두어야 한다.<br><br>

