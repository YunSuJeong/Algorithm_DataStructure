# Graph의 개념과 표현
> [✏️take a class✏️](https://www.inflearn.com/course/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EA%B0%95%EC%A2%8C/dashboard)
> 권오흠 교수님의 '영리한 프로그래밍을 위한 알고리즘 강좌' 인프런(inflearn) 강의를 듣고 정리한 내용입니다.


## 그래프 종류와 개념
### (무방향)그래프 G = (V, E)
- Undirectied Graph
- V, E는 각각 집합임
- 그래프의 **구성요소**
    - V : node(노드), vertex(정점)
    - E : 노드쌍을 연결하는 edge, link
- 개체(object)들 간의 이진관계를 표현
- n = |V|, m = |E|
- (1,2)과 (2,1)을 같게 봄
![undirected graph](https://github.com/user-attachments/assets/8042cd5a-fe9e-4307-b524-90ecd16e69db)

### 방향 그래프와 가중치 그래프 G = (V, E)
- Directed Graph
- 모든 엣지들이 방향을 가지고 있는 그래프
- 엣지를 화살표로 표시
- 에지 (u, v)는 u로부터 v로의 방향을 가짐
- (1,2)와 (2,1)을 다르게 봄
<img src="https://github.com/user-attachments/assets/32b647c8-0646-4e41-b581-5e2b03771b8a" width="450" height="400"/>

### 가중치 그래프
- Weighted Graph
- 방향 or 무방향 그래프일 수 있음
- 엣지마다 가중치가 지정


## 그래프의 표현
> 기본적으로 무방향 그래프 기준의 설명임
### 인접행렬 (adjacency matrix)
- N*N 행렬에 엣지를 1과 0으로 저장
- 저장 공간 : O(n<sup>2</sup>)
- 어떤 노드 v에 인접한 모든 노드 찾기 : O(n) 시간
- 어떤 에지 (u, v)가 존재하는지 검사 : O(1) 시간
![image](https://github.com/user-attachments/assets/a465666f-384a-47d9-ad09-25fdf425db8f)
` * 대칭행렬은 대각선으로 접었을 때, 만난다는 뜻으로 이해하면 됨 `

### 인접리스트 (adjacency list)
- 정점 집합을 표현하는 하나의 배열과 각 정점마다 인접한 정점들의 연결 리스트
- 연결리스트에 저장되는 정점의 순서는 중요하지 않음
- 저장 공간 : O(n+m)
  - 최악의 경우엔 O(n<sup>2</sup>) : n*(n-1)/2
- 어떤 노드 v에 인접한 모든 노드 찾기 : O(degree(v)) 시간
  - 최악의 경우엔 n-1개가 인접하여 있을 것이기 때문에, O(n)
  ` * degree(v) : 노드 v의 연결리스트의 길이 `
- 어떤 에지 (u, v)가 존재하는지 검사 : O(degree(u)) 시간
![image](https://github.com/user-attachments/assets/5e035a9d-f910-4e70-b2ed-e8b1cb57271f)
` * m은 edge의 개수 `

### 방향그래프의 표현
- 인접행렬은 비대칭
- 인접 리스트는 m개의 노드를 가짐
![image](https://github.com/user-attachments/assets/442aa7c1-e112-439f-8aeb-dfa533df011e)
` * self-edge : 자기 자신을 가리키고 있는 엣지, 위 그래프의 6번 노드 참고 '

### 가중치 그래프의 표현
**인접행렬**
- 에지의 존재를 나타내는 값으로 1대신 가중치를 저장
- 에지가 없을 때 혹은 대각선 :
  - 특별히 정해진 규칙은 없고, 그래프와 가중치가 의미하는 바에 따라 저장
  - ex1) 가중치가 거리 혹은 비용을 의미하는 경우 : 에지 없으면 무한대, 대각선은 0.
  - ex2) 가중치가 용량을 의미하는 경우 : 에지가 없을 때 0, 대각선은 무한대
  - ` * 대각선은 self-edge를 뜻함 `
 
## 그래프에서 사용하는 기본 용어들
- 무방향 그래프 G=(V, E)에서 노드 u와 노드 v를 연결하는 경로(path)가 존재할 때, **v와 u는 서로 연결되어 있다**고 말함
- **연결된(connected) 그래프** : 모든 노드 쌍들이 서로 연결된 그래프
- **연결요소(connected component)**
![image](https://github.com/user-attachments/assets/0dc3f612-8b2c-48ea-b176-3feb49c13026)
` * 위 그래프를 한 개의 그래프로 본다면, 각 덩어리들을 연결요소로 부른다. `
