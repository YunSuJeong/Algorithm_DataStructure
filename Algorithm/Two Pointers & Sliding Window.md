# Two Pointers (투 포인터 기법)
> 배열이나 리스트에서 **두 개의 포인터(인덱스)를 사용**하여 효율적으로 문제를 해결하는 방법  
> 주로 **정렬된 배열이나 연속된 구간을 탐색하는 문제**에서 사용

1. 두 개의 포인터(left, right)를 사용
2. 한 방향 또는 서로 다른 방향으로 이동
3. 이중 루프를 쓰지 않고 한 번의 순회로 해결 가능 -> O(n)으로 최적화

# Sliding Window(슬라이딩 윈도우)
> 고정된 크기 또는 가변적인 크기의 윈도우(구간)을 유지하며 이동하는 방식

1. 윈도우(window) = 연속된 구간
2. 윈도우의 크기를 유지하면서 이동(필요하면 크기 조절)
3. O(n)으로 최적화 가능



## 예제
### 백준
- [4158] [CD](https://www.acmicpc.net/problem/4158) : 두 포인터의 값만을 비교하는 문제 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/4158.%E2%80%85CD)
- [2018] [수들의 합 5](https://www.acmicpc.net/problem/2018) : 투 포인터를 이용하여 연속된 수들의 합이 M이되는 경우의 수 구하기 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/2018.%E2%80%85%EC%88%98%EB%93%A4%EC%9D%98%E2%80%85%ED%95%A9%E2%80%855)
- [11728] [배열 합치기](https://www.acmicpc.net/problem/11728) : 두 포인터의 값만을 비교하여 순서대로 출력하는 문제 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/11728.%E2%80%85%EB%B0%B0%EC%97%B4%E2%80%85%ED%95%A9%EC%B9%98%EA%B8%B0)
- [2003] [수들의 합 2](https://www.acmicpc.net/problem/2003) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/2003.%E2%80%85%EC%88%98%EB%93%A4%EC%9D%98%E2%80%85%ED%95%A9%E2%80%852)
- [1337] [올바른 배열](https://www.acmicpc.net/problem/1337) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1337.%E2%80%85%EC%98%AC%EB%B0%94%EB%A5%B8%E2%80%85%EB%B0%B0%EC%97%B4)
- [1940] [주몽](https://www.acmicpc.net/problem/1940) : 두 수의 합이 M인 경우의 수 구하기 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1940.%E2%80%85%EC%A3%BC%EB%AA%BD)
- [31589] [포도주 시음](https://www.acmicpc.net/problem/31589) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/31589.%E2%80%85%ED%8F%AC%EB%8F%84%EC%A3%BC%E2%80%85%EC%8B%9C%EC%9D%8C)
- [27931] [Parity Constraint Closest Pair (Easy)](https://www.acmicpc.net/problem/27931) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/27931.%E2%80%85Parity%E2%80%85Constraint%E2%80%85Closest%E2%80%85Pair%E2%80%85%EF%BC%88Easy%EF%BC%89)
- [28353] [고양이 카페](https://www.acmicpc.net/problem/28353) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/28353.%E2%80%85%EA%B3%A0%EC%96%91%EC%9D%B4%E2%80%85%EC%B9%B4%ED%8E%98)
- [21967] [세워라 반석 위에](https://www.acmicpc.net/problem/21967) : 슬라이딩 윈도우 방식까지 사용해야하는 문제 [소스 보기]()
- [29700] [우당탕탕 영화예매](https://www.acmicpc.net/problem/29700) : 슬라이딩 윈도우 사용 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/29700.%E2%80%85%EC%9A%B0%EB%8B%B9%ED%83%95%ED%83%95%E2%80%85%EC%98%81%ED%99%94%EC%98%88%EB%A7%A4)
- [24499] [blobyum](https://www.acmicpc.net/problem/24499) : 윈도우 크기가 고정인 슬라이딩 윈도우 문제 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/24499.%E2%80%85blobyum)
- [8933] [MCS](https://www.acmicpc.net/problem/8933) : 윈도우 크기 고정 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/8933.%E2%80%85MCS)
- [29718] [줄줄이 박수](https://www.acmicpc.net/problem/29718) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/29718.%E2%80%85%EC%A4%84%EC%A4%84%EC%9D%B4%E2%80%85%EB%B0%95%EC%88%98)
- [27496] [발머의 피크 이론](https://www.acmicpc.net/problem/27496) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/27496.%E2%80%85%EB%B0%9C%EB%A8%B8%EC%9D%98%E2%80%85%ED%94%BC%ED%81%AC%E2%80%85%EC%9D%B4%EB%A1%A0)
- [12847] [꿀 아르바이트](https://www.acmicpc.net/problem/12847) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/12847.%E2%80%85%EA%BF%80%E2%80%85%EC%95%84%EB%A5%B4%EB%B0%94%EC%9D%B4%ED%8A%B8)
- [10025] [게으른 백곰](https://www.acmicpc.net/problem/10025) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/10025.%E2%80%85%EA%B2%8C%EC%9C%BC%EB%A5%B8%E2%80%85%EB%B0%B1%EA%B3%B0)
- [21921] [블로그](https://www.acmicpc.net/problem/21921) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/21921.%E2%80%85%EB%B8%94%EB%A1%9C%EA%B7%B8)
- [2559] [수열](https://www.acmicpc.net/problem/2559) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2559.%E2%80%85%EC%88%98%EC%97%B4)
