# BFS & DFS
> [✏️take a class✏️](https://www.inflearn.com/courses/lecture?courseId=32456&unitId=4107&tab=curriculum) 권오흠 교수님의 '영리한 프로그래밍을 위한 알고리즘 강좌' 인프런(inflearn) 강의를 듣고 정리한 내용입니다.  
> 제공되는 자료는 없었기 때문에 이미지들은 직접 캡쳐하였습니다.

## 그래프 순회 (Graph Traversal)
- 그래프의 **모든 노드들을 방문**하는 일
- 대표적으로 BFS(너비우선순회), DFS(깊이우선순회) 2가지가 있다.

## BFS (Breadth-First Search)
### 순회 과정
1. L<sub>0</sub> = {s}, 여기서 s는 출발 노드
2. L<sub>1</sub> = L<sub>0</sub>의 모든 이웃 노드들
3. L<sub>2</sub> = L<sub>1</sub>의 이웃들 중 L<sub>0</sub>에 속하지 않는 노드들
4. L<sub>i</sub> = L<sub>i-1</sub>의 이웃들 중 L<sub>i-2</sub>에 속하지 않는 노드들  
<img src="https://github.com/user-attachments/assets/361721fe-31ce-47c0-9a25-fb7da0045625" width="400" height="250"/><br/>

### 큐를 이용한 순회 과정
<img src="https://github.com/user-attachments/assets/67240eb7-9e69-4a92-91d0-fe2ae9f54c78" width="400" height="250"/><br/>
<img src="https://github.com/user-attachments/assets/7caa6ab0-840d-4258-bf1d-2c90992134b1" width="400" height="250"/><br/>
`2,3 간의 탐색순서는 사실 별 크게 상관없다. 이것은 구현을 어떻게 하느냐에 따라 달라지는 것.!`  
<img src="https://github.com/user-attachments/assets/23ece10e-7c00-49dc-9cfd-9959a12933cf" width="400" height="250"/><br/>
<img src="https://github.com/user-attachments/assets/7a6df191-1b17-47de-8e56-8a034b56ca2c" width="400" height="250"/><br/>
<img src="https://github.com/user-attachments/assets/fc423a60-bd29-481b-b754-b258de37b674" width="400" height="250"/><br/>
<img src="https://github.com/user-attachments/assets/15ac5b66-8bf5-407c-90bb-5098deb61f5e" width="400" height="250"/><br/>
<img src="https://github.com/user-attachments/assets/0154f9e7-92b9-4e99-a664-160e9c7dcba8" width="400" height="250"/><br/>
<img src="https://github.com/user-attachments/assets/78352200-f596-4001-886e-650c73fd6b9c" width="400" height="250"/><br/>
`방문 순서는 유일한 방법은 아니며, 2/3같이 동일한 계층에서의 노드를 어떤 순서로 탐색하느냐에 따라 달라질 수 있다.`

### 구현
```java
// 그래프 G, 출발노드 s
BFS(G, s)        
  Q ← ∅;
  Enqueue(Q, s);                     // 큐에 넣는다 = enqueue
  while Q != ∅ do
    u ← Dequeue(Q)                   // 큐에서 꺼낸다 = dequeue
    for each v adjacent to u do      // 인접해있는 노드 탐색
      if v is unvisited then         // 방문한적 없는 노드라면, 방문처리 후 큐에 넣기
        mark v as visited;
        Enqueue(Q, v);
      end.
    end.
  end.
```

### 최단 경로
- s에서 L<sub>i</sub>에 속한 노드까지의 최단 경로의 길이는 i이다.
  - 경로의 길이 = 경로에 속한 엣지의 개수를 의미함.
- BFS로 각 노드에 대한 최단 경로 길이를 구할 수 있음

**구하는 과정**
- 입력 : 방향 혹은 무방향 그래프 G=(V, E), 출발노드 s∊V
- 출력 : 모든 노드 v에 대해
     - **d[v]** = s로 부터 v까지의 **최단 경로 길이 (엣지의 개수)**
     - **𝛑[v]** = s로 부터 v까지의 최단경로상에서 **v의 직전 노드**(predecessor)
- 인접리스트로 구현했을 때 시간복잡도  
<img src="https://github.com/user-attachments/assets/d1893bc7-f4d7-4287-a448-7c017af7adc8" width="250" height="50"/><br/>
`m : edge 개수`
     - while문을 한번 돌 때마다 큐에서 하나를 꺼내므로 while문은 최대 n번 반복
     - 인접리스트로 구현할 경우 for문은 각 노드 v에 대해 degree(v)번 반복  `degree : 실제 인접한 노드의 개수`
          - 인접행렬로 구현했을 땐 n번 반복하므로 O(n<sup>2</sup>)가 될 것임
```java
BFS(G, s)        
  Q ← ∅;
  // d[]의 값으로 unvisited/visited 상태 판단을 위한 초기화
  for each node u do
     d[u] ← -1;
     𝛑[s] ← null;
  end.

  d[s] ← 0;                          // distance from s to s is 0 
  𝛑[s] ← null;                       // no predecessor of s
  Enqueue(Q, s);

  while Q != ∅ do
    u ← Dequeue(Q)
    for each v adjacent to u do
      if v is unvisited then         // -1이면 unvisited
        mark v as visited;
        d[v] ← d[u] + 1;             // distance to v
        𝛑[v] ← u;                    // u is the predecessor of v
        Enqueue(Q, v);               // unchecked 노드만 queue에 들어갈 수 있으므로 어떤 노드도 큐에 두번 들어가지 않음
      end.
    end.
  end.
```

### BFS 트리
- 각 노드 v와 𝛑[v]를 연결하는 에지들로 구성된 트리
- BFS트리에서 s에서 v까지의 경로는 s에서 v까지 가는 최단경로
- 어떤 엣지도 2개의 layer를 건너가지 않는다. (동일 레이어의 노드를 연결 or 혹은 1개의 layer를 건너간다.)
<img src="https://github.com/user-attachments/assets/8870e048-82a3-41ed-95c2-5090eae0bc6a" width="400" height="250"/><br/>

### 최단 경로 출력하기
- 𝛑[v](=v의 직전노드)를 다 구해놓았다는 전제임
```java
// 출발점 s에서 노드 v까지의 경로 출력
PRINT-PATH(G, s, v)
  if v=s then
     print s;
  else if 𝛑[v]=null then                   // 그래프가 disconnected 일 때 
     print "no path from s to v exists";
  else
     PRINT-PATH(G, s, 𝛑[v]);               // recursion
     print v;
end.
```

### 만약 그래프가 disconnected 혹은 방향 그래프라면..?
BFS에 의해 모든 노드가 방문되지 않을 수 있다.  
이런 그래프에서 모든 노드를 방문해야한다면, **BFS를 반복하여 모든 노드를 방문**하면 된다.
```java
BFS-ALL( G ) {
  while there exists unvisited node v
     BFS(G, v);
}
```


## DFS (Depth-First Search)
### 순회 과정
1. 출발점 s에서 시작
2. 현재 노드를 visited로 mark하고 인접한 노드들 중 unvisited 노드가 존재하면 그 노드로 간다.
3. 2번을 계속 반복  
<img src="https://github.com/user-attachments/assets/5e954f15-6b9e-4193-92de-6eeaca360a34" width="300" height="300"/><br/>
4. 만약 unvisited인 이웃 노드가 존재하지 않는 동안 계속해서 직전 노드로 되돌아간다.  
<img src="https://github.com/user-attachments/assets/56b7e625-6dff-4c85-b820-81931e01f239" width="300" height="300"/><br/>
5. 다시 2번을 반복한다.  
<img src="https://github.com/user-attachments/assets/01e64c4b-5c30-498f-a704-1d8052c88983" width="300" height="300"/>
<img src="https://github.com/user-attachments/assets/d82b2ea8-e1aa-4571-be95-e2b437a9b2f8" width="300" height="300"/>
<img src="https://github.com/user-attachments/assets/672d9617-7b29-4adf-8763-c5fb876ae35f" width="300" height="300"/><br/>
6. 시작노드 s로 돌아오고 더 이상 갈 곳이 없으면 종료한다.<br/>
<img src="https://github.com/user-attachments/assets/8f6d6f71-84f5-45e3-a8eb-f3c0d0c99432" width="300" height="300"/><br/><br/>

**또 다른 예**  
```
// 탐색 순서 나타냄
A → B → E → I → J  
    B ← E ← I ← J  
    B → F → C → A → D → G → H
                A ← D ← G ← H
```
![image](https://github.com/user-attachments/assets/d92274c8-e88e-48f5-8e18-fbe2c32f66f6)

### 구현 (recursion)
```java
DFS(G, v)
  visited[v] ← YES;                  // 이미 방문한 노드로 마크
  for each node u adjacent to v do    // v에 인접한 노드 u 탐색하면서
    if visited[u] = NO then           // 방문하지 않은 노드라면
      DFS(G, u)
  end.
end.
```

**disconnected 그래프, 방향 그래프일 때 깊이우선 탐색하기**
- 모든 노드가 방문되지 않을 수도 있기 때문에, DFS를 반복하여 모든 노드에 방문할 수 있도록 한다.
- 시간복잡도
  - 인접리스트로 노드 구현 시 : O(n+m)
    - n : 모든 노드를 세팅하는데 걸리는 시간
    - m : 재귀호출하는 횟수, 방문한 노드는 다시 방문하지 않기 때문에 호출 횟수는 엣지의 개수에 비례함 (엣지 1개당 호출 1번으로 생각하면 된다.)
  - 인접행렬로 노드를 구현 시 : O(n<sup>2</sup>)
```java
DFS-ALL(G) {
  for each V ∊ V
    visited[v] ← NO;
  for each V ∊ V                    // 모든 노드에 대해서
    if( visited[v] = NO ) then      // 방문되지 않은 노드가 있다면
      DFS(G, v);                    // 다시 탐색
}
```

## 예제
### 백준
- [10974] [모든 순열](https://www.acmicpc.net/problem/10974) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/10974.%E2%80%85%EB%AA%A8%EB%93%A0%E2%80%85%EC%88%9C%EC%97%B4)
- [24479] [알고리즘 수업 - 깊이 우선 탐색 1](https://www.acmicpc.net/problem/24479) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/24479.%E2%80%85%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%E2%80%85%EC%88%98%EC%97%85%E2%80%85%EF%BC%8D%E2%80%85%EA%B9%8A%EC%9D%B4%E2%80%85%EC%9A%B0%EC%84%A0%E2%80%85%ED%83%90%EC%83%89%E2%80%851)
- [24480] [알고리즘 수업 - 깊이 우선 탐색 2](https://www.acmicpc.net/problem/24480) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/24480.%E2%80%85%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%E2%80%85%EC%88%98%EC%97%85%E2%80%85%EF%BC%8D%E2%80%85%EA%B9%8A%EC%9D%B4%E2%80%85%EC%9A%B0%EC%84%A0%E2%80%85%ED%83%90%EC%83%89%E2%80%852)
- [11558] [The Game of Death](https://www.acmicpc.net/problem/11558) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/11558.%E2%80%85The%E2%80%85Game%E2%80%85of%E2%80%85Death)
- [2606] [바이러스](https://www.acmicpc.net/problem/2606) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2606.%E2%80%85%EB%B0%94%EC%9D%B4%EB%9F%AC%EC%8A%A4)
- [1182] [부분수열의 합](https://www.acmicpc.net/problem/1182) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1182.%E2%80%85%EB%B6%80%EB%B6%84%EC%88%98%EC%97%B4%EC%9D%98%E2%80%85%ED%95%A9)
- [31575] [도시와 비트코인](https://www.acmicpc.net/problem/31575) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/31575.%E2%80%85%EB%8F%84%EC%8B%9C%EC%99%80%E2%80%85%EB%B9%84%ED%8A%B8%EC%BD%94%EC%9D%B8)
- [16173] [점프왕 쩰리 (Small)](https://www.acmicpc.net/problem/16173) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/16173.%E2%80%85%EC%A0%90%ED%94%84%EC%99%95%E2%80%85%EC%A9%B0%EB%A6%AC%E2%80%85%EF%BC%88Small%EF%BC%89)
- [26169] [세 번 이내에 사과를 먹자](https://www.acmicpc.net/problem/26169) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/26169.%E2%80%85%EC%84%B8%E2%80%85%EB%B2%88%E2%80%85%EC%9D%B4%EB%82%B4%EC%97%90%E2%80%85%EC%82%AC%EA%B3%BC%EB%A5%BC%E2%80%85%EB%A8%B9%EC%9E%90)
- [26170] [사과 빨리 먹기](http://acmicpc.net/problem/26170) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/26170.%E2%80%85%EC%82%AC%EA%B3%BC%E2%80%85%EB%B9%A8%EB%A6%AC%E2%80%85%EB%A8%B9%EA%B8%B0)
- [25516] [거리가 k이하인 트리 노드에서 사과 수확하기](https://www.acmicpc.net/problem/25516) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25516.%E2%80%85%EA%B1%B0%EB%A6%AC%EA%B0%80%E2%80%85k%EC%9D%B4%ED%95%98%EC%9D%B8%E2%80%85%ED%8A%B8%EB%A6%AC%E2%80%85%EB%85%B8%EB%93%9C%EC%97%90%EC%84%9C%E2%80%85%EC%82%AC%EA%B3%BC%E2%80%85%EC%88%98%ED%99%95%ED%95%98%EA%B8%B0)
- [18126] [너구리 구구](https://www.acmicpc.net/problem/18126) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/18126.%E2%80%85%EB%84%88%EA%B5%AC%EB%A6%AC%E2%80%85%EA%B5%AC%EA%B5%AC)
- [21938] [영상처리](https://www.acmicpc.net/problem/21938) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/21938.%E2%80%85%EC%98%81%EC%83%81%EC%B2%98%EB%A6%AC)
- [14248] [점프 점프](https://www.acmicpc.net/problem/14248) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14248.%E2%80%85%EC%A0%90%ED%94%84%E2%80%85%EC%A0%90%ED%94%84)
- [11123] [양 한마리... 양 두마리...](https://www.acmicpc.net/problem/11123) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11123.%E2%80%85%EC%96%91%E2%80%85%ED%95%9C%EB%A7%88%EB%A6%AC%EF%BC%8E%EF%BC%8E%EF%BC%8E%E2%80%85%EC%96%91%E2%80%85%EB%91%90%EB%A7%88%EB%A6%AC%EF%BC%8E%EF%BC%8E%EF%BC%8E)
- [13565] [침투](https://www.acmicpc.net/problem/13565) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/13565.%E2%80%85%EC%B9%A8%ED%88%AC)
- [2210] [숫자판 점프](https://www.acmicpc.net/problem/2210) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2210.%E2%80%85%EC%88%AB%EC%9E%90%ED%8C%90%E2%80%85%EC%A0%90%ED%94%84)
- [21736] [헌내기는 친구가 필요해](https://www.acmicpc.net/problem/21736) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/21736.%E2%80%85%ED%97%8C%EB%82%B4%EA%B8%B0%EB%8A%94%E2%80%85%EC%B9%9C%EA%B5%AC%EA%B0%80%E2%80%85%ED%95%84%EC%9A%94%ED%95%B4)
- [2644] [촌수계산](https://www.acmicpc.net/problem/2644) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2644.%E2%80%85%EC%B4%8C%EC%88%98%EA%B3%84%EC%82%B0)
- [25416] [빠른 숫자 탐색](https://www.acmicpc.net/problem/25416) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25416.%E2%80%85%EB%B9%A0%EB%A5%B8%E2%80%85%EC%88%AB%EC%9E%90%E2%80%85%ED%83%90%EC%83%89)
- [4963] [섬의 개수](https://www.acmicpc.net/problem/4963) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/4963.%E2%80%85%EC%84%AC%EC%9D%98%E2%80%85%EA%B0%9C%EC%88%98)
- [9079] [동전 게임](https://www.acmicpc.net/problem/9079) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/9079.%E2%80%85%EB%8F%99%EC%A0%84%E2%80%85%EA%B2%8C%EC%9E%84)
- [11725] [트리의 부모 찾기](https://www.acmicpc.net/problem/11725) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11725.%E2%80%85%ED%8A%B8%EB%A6%AC%EC%9D%98%E2%80%85%EB%B6%80%EB%AA%A8%E2%80%85%EC%B0%BE%EA%B8%B0)
- [11724] [연결 요소의 개수](https://www.acmicpc.net/problem/11724) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11724.%E2%80%85%EC%97%B0%EA%B2%B0%E2%80%85%EC%9A%94%EC%86%8C%EC%9D%98%E2%80%85%EA%B0%9C%EC%88%98)
- [1012] [유기농 배추](https://www.acmicpc.net/problem/1012) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1012.%E2%80%85%EC%9C%A0%EA%B8%B0%EB%86%8D%E2%80%85%EB%B0%B0%EC%B6%94)
- [1260] [DFS와 BFS](https://www.acmicpc.net/problem/1260) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1260.%E2%80%85DFS%EC%99%80%E2%80%85BFS)
- [15270] [친구 팰린드롬](https://www.acmicpc.net/problem/15270) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/15270.%E2%80%85%EC%B9%9C%EA%B5%AC%E2%80%85%ED%8C%B0%EB%A6%B0%EB%93%9C%EB%A1%AC)
- [14496] [그대, 그머가 되어](https://www.acmicpc.net/problem/14496) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14496.%E2%80%85%EA%B7%B8%EB%8C%80%EF%BC%8C%E2%80%85%EA%B7%B8%EB%A8%B8%EA%B0%80%E2%80%85%EB%90%98%EC%96%B4)
- [17086] [아기 상어 2](https://www.acmicpc.net/problem/17086) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/17086.%E2%80%85%EC%95%84%EA%B8%B0%E2%80%85%EC%83%81%EC%96%B4%E2%80%852)
- [1326] [폴짝폴짝](https://www.acmicpc.net/problem/1326) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1326.%E2%80%85%ED%8F%B4%EC%A7%9D%ED%8F%B4%EC%A7%9D)
- [18232] [텔레포트 정거장](https://www.acmicpc.net/problem/18232) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/18232.%E2%80%85%ED%85%94%EB%A0%88%ED%8F%AC%ED%8A%B8%E2%80%85%EC%A0%95%EA%B1%B0%EC%9E%A5)
- [14218] [그래프 탐색 2](https://www.acmicpc.net/problem/14218) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14218.%E2%80%85%EA%B7%B8%EB%9E%98%ED%94%84%E2%80%85%ED%83%90%EC%83%89%E2%80%852)
- [27737] [https://www.acmicpc.net/problem/27737](https://www.acmicpc.net/problem/27737) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/27737.%E2%80%85%EB%B2%84%EC%84%AF%E2%80%85%EB%86%8D%EC%9E%A5)
- [17198] [Bucket Brigade](https://www.acmicpc.net/problem/17198) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/17198.%E2%80%85Bucket%E2%80%85Brigade)
- [31946] [죽음의 등굣길](https://www.acmicpc.net/problem/31946) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/31946.%E2%80%85%EC%A3%BD%EC%9D%8C%EC%9D%98%E2%80%85%EB%93%B1%EA%B5%A3%EA%B8%B8)
- [15723] [n단 논법](https://www.acmicpc.net/problem/15723) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/15723.%E2%80%85n%EB%8B%A8%E2%80%85%EB%85%BC%EB%B2%95)
- [30106] [현이의 로봇 청소기](https://www.acmicpc.net/problem/30106) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/30106.%E2%80%85%ED%98%84%EC%9D%B4%EC%9D%98%E2%80%85%EB%A1%9C%EB%B4%87%E2%80%85%EC%B2%AD%EC%86%8C%EA%B8%B0)
- [21937] [작업](https://www.acmicpc.net/problem/21937) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/21937.%E2%80%85%EC%9E%91%EC%97%85)
- [11581] [구호물자](https://www.acmicpc.net/problem/11581) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11581.%E2%80%85%EA%B5%AC%ED%98%B8%EB%AC%BC%EC%9E%90)
- [15900] [나무 탈출](https://www.acmicpc.net/problem/15900) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/15900.%E2%80%85%EB%82%98%EB%AC%B4%E2%80%85%ED%83%88%EC%B6%9C)
- [16953] [A → B](https://www.acmicpc.net/problem/16953) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/16953.%E2%80%85A%E2%80%85%E2%86%92%E2%80%85B)
- [18352] [특정 거리의 도시 찾기](https://www.acmicpc.net/problem/18352) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/18352.%E2%80%85%ED%8A%B9%EC%A0%95%E2%80%85%EA%B1%B0%EB%A6%AC%EC%9D%98%E2%80%85%EB%8F%84%EC%8B%9C%E2%80%85%EC%B0%BE%EA%B8%B0)
- [14716] [현수막](https://www.acmicpc.net/problem/14716) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14716.%E2%80%85%ED%98%84%EC%88%98%EB%A7%89)
- [31564] [육각타일미로 탈출기](https://www.acmicpc.net/problem/31564) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/31564.%E2%80%85%EC%9C%A1%EA%B0%81%ED%83%80%EC%9D%BC%EB%AF%B8%EB%A1%9C%E2%80%85%ED%83%88%EC%B6%9C%EA%B8%B0)
- [3187] [양치기 꿍](https://www.acmicpc.net/problem/3187) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/3187.%E2%80%85%EC%96%91%EC%B9%98%EA%B8%B0%E2%80%85%EA%BF%8D)

### SWEA
- [6808] [규영이와 인영이의 카드게임](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AWgv9va6HnkDFAW0&categoryId=AWgv9va6HnkDFAW0&categoryType=CODE&problemTitle=&orderBy=RECOMMEND_COUNT&selectCodeLang=ALL&select-1=3&pageSize=30&pageIndex=1&&&&&&&&&&) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/6808.%E2%80%85%EA%B7%9C%EC%98%81%EC%9D%B4%EC%99%80%E2%80%85%EC%9D%B8%EC%98%81%EC%9D%B4%EC%9D%98%E2%80%85%EC%B9%B4%EB%93%9C%EA%B2%8C%EC%9E%84)
- [2817] [부분 수열의 합](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AV7IzvG6EksDFAXB&categoryId=AV7IzvG6EksDFAXB&categoryType=CODE&problemTitle=&orderBy=RECOMMEND_COUNT&selectCodeLang=ALL&select-1=3&pageSize=30&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/2817.%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4%EC%9D%98%E2%80%85%ED%95%A9)
- [2814] [최장 경로](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AV7GOPPaAeMDFAXB&categoryId=AV7GOPPaAeMDFAXB&categoryType=CODE&problemTitle=&orderBy=RECOMMEND_COUNT&selectCodeLang=ALL&select-1=3&pageSize=30&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/2814.%E2%80%85%EC%B5%9C%EC%9E%A5%E2%80%85%EA%B2%BD%EB%A1%9C)
