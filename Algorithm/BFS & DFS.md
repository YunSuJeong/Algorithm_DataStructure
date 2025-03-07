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

### SWEA
- [6808] [규영이와 인영이의 카드게임](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AWgv9va6HnkDFAW0&categoryId=AWgv9va6HnkDFAW0&categoryType=CODE&problemTitle=&orderBy=RECOMMEND_COUNT&selectCodeLang=ALL&select-1=3&pageSize=30&pageIndex=1&&&&&&&&&&) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/6808.%E2%80%85%EA%B7%9C%EC%98%81%EC%9D%B4%EC%99%80%E2%80%85%EC%9D%B8%EC%98%81%EC%9D%B4%EC%9D%98%E2%80%85%EC%B9%B4%EB%93%9C%EA%B2%8C%EC%9E%84)
- [2817] [부분 수열의 합](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AV7IzvG6EksDFAXB&categoryId=AV7IzvG6EksDFAXB&categoryType=CODE&problemTitle=&orderBy=RECOMMEND_COUNT&selectCodeLang=ALL&select-1=3&pageSize=30&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/2817.%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4%EC%9D%98%E2%80%85%ED%95%A9)
