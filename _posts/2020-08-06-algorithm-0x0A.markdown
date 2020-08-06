---
layout: post
title: "DFS"
date:   2020-08-06 19:00
categories: ["barkingDog"]
author: "J-Shine"
---

# 바킹독님의 실전알고리즘배우기 10강듣고 요약
[바킹독의 실전 알고리즘 10강 링크](https://blog.encrypted.gg/942)   
 
![image](https://user-images.githubusercontent.com/61873510/89512173-ce90ec00-d80d-11ea-98ac-9ee145917ade.png)<br>
![image](https://user-images.githubusercontent.com/61873510/89512219-dea8cb80-d80d-11ea-9e74-f9f1e9edeab0.png)<br><br>

# DFS 과정
![image](https://user-images.githubusercontent.com/61873510/89512788-afdf2500-d80e-11ea-870e-3f4399a324ea.png)<br>
DFS는 깊이우선탐색 알고리즘으로, **스택**을 이용한다.<br>
BFS가 여러 가지를 조금씩 건드리며 점점 깊게 가는 것과는 달리, DFS는 한 가지를 일단 깊게 파고들고나서 끝에 도달하면 인접한 다른 가지로 가는 식이다.<br>
구현 방법은 BFS와 같고, 큐 대신 스택을 이용하여 구현하면 된다.<br><br>

# DFS 코드 예시
![image](https://user-images.githubusercontent.com/61873510/89513777-f7b27c00-d80f-11ea-8d4f-8a0774f4dbff.png)<br>
위 그림의 파란색 칸을 DFS로 모두 탐색하는 코드<br><br>

```c++
#include <bits/stdc++.h>
using namespace std;
#define X first
#define Y second // pair에서 first, second를 줄여서 쓰기 위해서 사용

// 문제에서 파란칸은 1, 빨간칸은 0으로 board에 설정 (블로그에 올릴 때 자꾸 오류가 떠서 지웠음)

bool vis[502][502]; // 해당 칸을 방문했는지 여부를 저장
int n = 7, m = 10; // n = 행의 수, m = 열의 수
int dx[4] = {1,0,-1,0};
int dy[4] = {0,1,0,-1}; // 상하좌우 네 방향을 의미
int main(void){
  ios::sync_with_stdio(0);
  cin.tie(0);
  stack<pair<int,int> > S;
  vis[0][0] = 1; // (0, 0)을 방문했다고 명시
  S.push({0,0}); // 스택에 시작점인 (0, 0)을 삽입.
  while(!S.empty()){
    pair<int,int> cur = S.top(); S.pop();
    cout << '(' << cur.X << ", " << cur.Y << ") -> ";
    for(int dir = 0; dir < 4; dir++){ // 상하좌우 칸을 살펴볼 것이다.
      int nx = cur.X + dx[dir];
      int ny = cur.Y + dy[dir]; // nx, ny에 dir에서 정한 방향의 인접한 칸의 좌표가 들어감
      if(nx < 0 || nx >= n || ny < 0 || ny >= m) continue; // 범위 밖일 경우 넘어감
      if(vis[nx][ny] || board[nx][ny] != 1) continue; // 이미 방문한 칸이거나 파란 칸이 아닐 경우
      vis[nx][ny] = 1; // (nx, ny)를 방문했다고 명시
      S.push({nx,ny});
    }
  }
}
```
자세한건 주석에 설명<br>
DFS를 돌릴 때는 보통 n과 x가 행이고, m과 y가 열이다.<br>
**그리고 위의 #define X first, #define Y second를 할 때 끝에 세미콜론이 붙지 않는다!!**<br>
세미콜론을 붙이면 define한 X, Y 사용시 에러가 나므로 주의<br><br>

