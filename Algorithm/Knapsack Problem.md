# Knapsack Problem (배낭 문제)
주어진 **무게 제한(또는 용량) 내**에서 **최대한의 가치**를 얻는 최적화 문제로, 대표적인 DP문제이다.

## 접근 방식
> 담을 수 있는 물건이 나뉠 수 있는가, 없는가?
- 나뉠 수 **있다** : **분할가능 배낭문제 (Fractional Knapsack Problem)**
- 나뉠 수 **없다** : **0-1 배낭 문제(0-1 Knapsack Problem)**

## 0-1 배낭 문제 (0-1 배낭 문제)
> N개 물건의 무게와 가치가 주어진다.
> 10kg까지 담을 수 있는 배낭에 담을 수 있는 최대 이익을 구하라

### 이게 어떻게 DP문제일까?
사실 배낭 문제가 대표적인 dp문제임을 모르고 풀었을 땐, dfs로 접근하여 풀었었다.  
현재 배낭에 물건을 넣을 수 있다면 넣고, 넣을 수 없다면 넣지 않는다는 것에 포인트를 잡고 모든 경우를 탐색하며 최대 이익을 구하는 방법밖에 생각나지 않았다..  
사실 포인트는 조금 잘 짚었다고 할 수 있겠다.!  
**물건을 넣거나, 말거나!**

조금 더 생각해보자. 간단히 생각해보기위해 일단 가치는 생각하지 않는다.  
10kg에 6kg짜리 물건을 넣었다면 그다음에 넣을 수 있는 무게는 최대 4kg짜리 물건이다.  
그럼 그 다음 단계에선 남은 4kg 공간에 2kg짜리 물건을 넣으면 최대 2kg짜리 물건을 넣을 수 있다.  
**10kg = 6kg 물건 + (4kg 공간 = 2kg물건 + (2kg 공간 + ...))** 이렇게 생각해 볼 수 있다.!

가치는 빼고 생각해보았지만 사실 가치가 들어가도 같다.  
**10kg에 넣을 수 있는 물건의 최대 이익 = 6kg + (4kg 공간에 담을 수 있는 물건의 최대 이익 = 2kg + (2kg 공간에 담을 수 있는 최대 이익))  **
부분의 답이 큰 부분의 답이 되고 이 부분들의 답이 전체의 답이 되므로 dp로 풀 수 있는 것 아니겠는가!

### 점화식 유도
- 변수
  - 배낭 남은 공간(W)
  - 담을 수 있는 물건의 개수(i)  
- DP[i][W] : Wkg 가방에 i번째 물건까지 탐색했을 때의 최대 이익

**1. i번째 물건의 무게 > 배낭의 남은 공간**
> 이 경우엔 배낭에 i번째 물건을 넣을 수 없다.
- 최대 이익은 이전 최대 이익과 같다.
- DP[i][w] = DP[i-1][w]

**2. i번째 물건의 무게 <= 배낭의 남은 공간** 
> 두 가지 선택이 존재한다. 두 선택 중 더 큰 이익을 택한다. 
- i번째 물건을 넣는다.
  - DP[i][w] = (i번째 물건의 이익) + DP[i-1][w-(i번째 물건의 무게)]
- i번째 물건을 안 넣는다.
  - DP[i][w] = DP[i-1][w]


## 분할가능 배낭문제 (Fractional Knapsack Problem)
추후 정리 예정입니다.

## 예제
### 백준
- [16493] [최대 페이지 수](https://www.acmicpc.net/problem/16493) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/16493.%E2%80%85%EC%B5%9C%EB%8C%80%E2%80%85%ED%8E%98%EC%9D%B4%EC%A7%80%E2%80%85%EC%88%98)

### SWEA
- [5215] [햄버거 다이어트](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWT-lPB6dHUDFAVT&categoryId=AWT-lPB6dHUDFAVT&categoryType=CODE&problemTitle=5215&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=&pageSize=10&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/5215.%E2%80%85%ED%96%84%EB%B2%84%EA%B1%B0%E2%80%85%EB%8B%A4%EC%9D%B4%EC%96%B4%ED%8A%B8)
- [3282] [0/1 Knapsack](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWBJAVpqrzQDFAWr&categoryId=AWBJAVpqrzQDFAWr&categoryType=CODE&problemTitle=3282&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=&pageSize=10&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/3282.%E2%80%850%EF%BC%8F1%E2%80%85Knapsack)

## 출처
- [이니의 공부일지:티스토리](https://inni-iii.tistory.com/74)
- [호우동의 개발일지](https://howudong.tistory.com/106)
