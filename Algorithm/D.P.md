# 동적계획법(Dynamic Programming)
  복잡한 문제를 더 작은 문제로 나누어 해결한다.

## Dynamic Programing VS Divide and Conquer
  동적계획법은 분할정복법과 문제를 해결하기 위해 더 작은 문제로 나눈다는 점에서는 유사하지만 다르다.  
  어떤 점에서 다를까?

  1. 접근 방식의 차이  
  **D.P** -> 주로 **Bottom-Up(상향식)** 방식으로 접근 (Top-Down으로도 구현가능하다. 아래 구현방법 참고)
  **Divide and Conquer** -> **Top-Down(하향식)** 방식으로 접근
  
  2. 메모이제이션(**Memoization**) 기법 사용  
  계산결과를 저장하는 메모리 기법  
  저장되어있는 결과를 다시 가져다 사용함으로써 재귀호출에서의 중복 계산을 방지하고 속도를 향상시킨다.

## DP 장단점
  - 장점
    - 중복계산을 줄일 수 있다.
    - 효율적인 시간복잡도를 가진다.
  - 단점
    - 중간결과를 저장하기 위한 추가 메모리가 필요하기 때문에 메모리 사용량이 크다. 문제의 크기가 커질수록 필요한 메모리가 증가할 수 있다.

## DP 사용가능한 조건
  1. Overlapping Subproblems = 동일한 부분 문제가 있는지
  2. Optimal Substructure = 부분 문제의 최적의 답을 이용하여 구한 최종적 답이 최적의 답이 되는지

## 구현방법
  1. Bottom-Up(Tabulation 방식) : 반복문 사용
  2. Top-Down(Memoization 방식) : 재귀 사용

## 예제

### 백준
- [11727] [2×n 타일링 2](https://www.acmicpc.net/problem/11727) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/11727.%E2%80%852%C3%97n%E2%80%85%ED%83%80%EC%9D%BC%EB%A7%81%E2%80%852)

[참고] https://hongjw1938.tistory.com/47

      
