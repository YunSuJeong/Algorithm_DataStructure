# Fibonacci numbers(피보나치 수열)

## 피보나치 수열이란?
> 이전 두 항의 합이 다음 항이 되는 수열  
> 첫째 항과 두번째 항 = 1

  
## 점화식
> F(1) = F(2) = 1  
> **F(n) = F(n-1) + F(n-2)** (단, n > 2)

  
## 구현 방법
### 재귀함수 이용
```
fibonacci( n ) {
  if( n == 1 or n == 2 )
    return 1;
  else
    fabonacci(n-1) + fibonacci(n-2);
}
```

### DP 이용
```
for(int i=1; i<=N; i++) {
  if( i < 3 )
    fib[i] = 1;
  else
    fib[i] = fib[i-1] + fib[i-2];
}
```

### 구현 방법 비교
|  | 재귀함수 | DP |
|---|---|---|
| 시간복잡도 | O(N^2) | O(N) |
| 장점 | 구현이 쉽다. | 이미 계산한 값을 사용하여 실행시간을 줄일 수 있다. |
| 단점 | 시간복잡도가 높아 큰 수 계산하기 어렵다. | 메모리 사용량이 높아질 수 있다. |



## 예제
### 백준
- [24416] [알고리즘 수업 - 피보나치 수 1](https://www.acmicpc.net/problem/24416) : 재귀호출과 DP의 실행횟수 비교 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Bronze/24416.%E2%80%85%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%E2%80%85%EC%88%98%EC%97%85%E2%80%85%EF%BC%8D%E2%80%85%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98%E2%80%85%EC%88%98%E2%80%851)
- [1904] [01타일](https://www.acmicpc.net/problem/1904) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1904.%E2%80%8501%ED%83%80%EC%9D%BC)
