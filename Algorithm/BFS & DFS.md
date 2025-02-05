# BFS & DFS
> [✏️take a class✏️](https://www.inflearn.com/courses/lecture?courseId=32456&unitId=4107&tab=curriculum) 권오흠 교수님의 '영리한 프로그래밍을 위한 알고리즘 강좌' 인프런(inflearn) 강의를 듣고 정리한 내용입니다.

## 그래프 순회 (Graph Traversal)
- 그래프의 **모든 노드들을 방문**하는 일
- 대표적으로 BFS(너비우선순회), DFS(깊이우선순회) 2가지가 있다.

## BFS (Breadth-First Search)


## DFS (Depth-First Search)
### 개념
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
A -> B -> E -> I -> J  
     B <- E <- I <- J  
     B -> F -> C -> A -> D -> G -> H
                    A <- D <- G <- H
```
![image](https://github.com/user-attachments/assets/d92274c8-e88e-48f5-8e18-fbe2c32f66f6)

### 구현 (recursion)
```java
DFS(G, v)
  visited[v] <- YES;                  // 이미 방문한 노드로 마크
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
    visited[v] <- NO;
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
