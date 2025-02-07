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
- [2579] [계단 오르기](https://www.acmicpc.net/problem/2579) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/2579.%E2%80%85%EA%B3%84%EB%8B%A8%E2%80%85%EC%98%A4%EB%A5%B4%EA%B8%B0)
- [9461] [파도반 수열](https://www.acmicpc.net/problem/9461) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/9461.%E2%80%85%ED%8C%8C%EB%8F%84%EB%B0%98%E2%80%85%EC%88%98%EC%97%B4)
- [9095] [1, 2, 3 더하기](https://www.acmicpc.net/problem/9095) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/9095.%E2%80%851%EF%BC%8C%E2%80%852%EF%BC%8C%E2%80%853%E2%80%85%EB%8D%94%ED%95%98%EA%B8%B0)
- [2193] [이친수](https://www.acmicpc.net/problem/2193) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/2193.%E2%80%85%EC%9D%B4%EC%B9%9C%EC%88%98)
- [1699] [제곱수의 합](https://www.acmicpc.net/problem/1699) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1699.%E2%80%85%EC%A0%9C%EA%B3%B1%EC%88%98%EC%9D%98%E2%80%85%ED%95%A9)
- [17626] [Four Squares](https://www.acmicpc.net/problem/17626) : 1699와 같은 유형 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/17626.%E2%80%85Four%E2%80%85Squares)
- [9184] [신나는 함수 실행](https://www.acmicpc.net/problem/9184) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/9184.%E2%80%85%EC%8B%A0%EB%82%98%EB%8A%94%E2%80%85%ED%95%A8%EC%88%98%E2%80%85%EC%8B%A4%ED%96%89)
- [1912] [연속합](https://www.acmicpc.net/problem/1912) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1912.%E2%80%85%EC%97%B0%EC%86%8D%ED%95%A9)

[참고] https://hongjw1938.tistory.com/47

      
