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
- [4158] CD : 두 포인터의 값만을 비교하는 문제 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/4158.%E2%80%85CD)
- [2018] 수들의 합 5 : 투 포인터를 이용하여 연속된 수들의 합이 M이되는 경우의 수 구하기 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/2018.%E2%80%85%EC%88%98%EB%93%A4%EC%9D%98%E2%80%85%ED%95%A9%E2%80%855)
- [11728] 배열 합치기 : 두 포인터의 값만을 비교하여 순서대로 출력하는 문제 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/11728.%E2%80%85%EB%B0%B0%EC%97%B4%E2%80%85%ED%95%A9%EC%B9%98%EA%B8%B0)
- [2003] 수들의 합 2 : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/2003.%E2%80%85%EC%88%98%EB%93%A4%EC%9D%98%E2%80%85%ED%95%A9%E2%80%852)
- [1337] 올바른 배열 : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1337.%E2%80%85%EC%98%AC%EB%B0%94%EB%A5%B8%E2%80%85%EB%B0%B0%EC%97%B4)
- [1940] 주몽 : 두 수의 합이 M인 경우의 수 구하기 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1940.%E2%80%85%EC%A3%BC%EB%AA%BD)
- [31589] 포도주 시음 : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/31589.%E2%80%85%ED%8F%AC%EB%8F%84%EC%A3%BC%E2%80%85%EC%8B%9C%EC%9D%8C)
- [27931] Parity Constraint Closest Pair (Easy) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/27931.%E2%80%85Parity%E2%80%85Constraint%E2%80%85Closest%E2%80%85Pair%E2%80%85%EF%BC%88Easy%EF%BC%89)
- [28353] 고양이 카페 : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/28353.%E2%80%85%EA%B3%A0%EC%96%91%EC%9D%B4%E2%80%85%EC%B9%B4%ED%8E%98)
- [21967] 세워라 반석 위에 : 슬라이딩 윈도우 방식까지 사용해야하는 문제 [소스 보기]()
- [29700] 우당탕탕 영화예매 : 슬라이딩 윈도우 사용 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/29700.%E2%80%85%EC%9A%B0%EB%8B%B9%ED%83%95%ED%83%95%E2%80%85%EC%98%81%ED%99%94%EC%98%88%EB%A7%A4)
- [24499] blobyum : 윈도우 크기가 고정인 슬라이딩 윈도우 문제 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/24499.%E2%80%85blobyum)
- [8933] MCS : 윈도우 크기 고정 [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/8933.%E2%80%85MCS)
- [29718] 줄줄이 박수 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/29718.%E2%80%85%EC%A4%84%EC%A4%84%EC%9D%B4%E2%80%85%EB%B0%95%EC%88%98)
- [27496] 발머의 피크 이론 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/27496.%E2%80%85%EB%B0%9C%EB%A8%B8%EC%9D%98%E2%80%85%ED%94%BC%ED%81%AC%E2%80%85%EC%9D%B4%EB%A1%A0)
- [12847] 꿀 아르바이트 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/12847.%E2%80%85%EA%BF%80%E2%80%85%EC%95%84%EB%A5%B4%EB%B0%94%EC%9D%B4%ED%8A%B8)
- [10025] 게으른 백곰 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/10025.%E2%80%85%EA%B2%8C%EC%9C%BC%EB%A5%B8%E2%80%85%EB%B0%B1%EA%B3%B0)
- [21921] 블로그 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/21921.%E2%80%85%EB%B8%94%EB%A1%9C%EA%B7%B8)
- [2559] 수열 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2559.%E2%80%85%EC%88%98%EC%97%B4)
- [14465] 소가 길을 건너간 이유 5 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14465.%E2%80%85%EC%86%8C%EA%B0%80%E2%80%85%EA%B8%B8%EC%9D%84%E2%80%85%EA%B1%B4%EB%84%88%EA%B0%84%E2%80%85%EC%9D%B4%EC%9C%A0%E2%80%855)
- [12891] DNA 비밀번호 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/12891.%E2%80%85DNA%E2%80%85%EB%B9%84%EB%B0%80%EB%B2%88%ED%98%B8)
- [26050] Patio : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/26050.%E2%80%85Patio)
- [25979] 시간 구간 다중 업데이트 최대 합 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25979.%E2%80%85%EC%8B%9C%EA%B0%84%E2%80%85%EA%B5%AC%EA%B0%84%E2%80%85%EB%8B%A4%EC%A4%91%E2%80%85%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8%E2%80%85%EC%B5%9C%EB%8C%80%E2%80%85%ED%95%A9)
- [9549] 암호화된 비밀번호 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/9549.%E2%80%85%EC%95%94%ED%98%B8%ED%99%94%EB%90%9C%E2%80%85%EB%B9%84%EB%B0%80%EB%B2%88%ED%98%B8)
- [33043] 이변마작 9 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/33043.%E2%80%85%EC%9D%B4%EB%B3%80%EB%A7%88%EC%9E%91%E2%80%859)
- [27527] 배너 걸기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/27527.%E2%80%85%EB%B0%B0%EB%84%88%E2%80%85%EA%B1%B8%EA%B8%B0)
- [15565] 귀여운 라이언 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/15565.%E2%80%85%EA%B7%80%EC%97%AC%EC%9A%B4%E2%80%85%EB%9D%BC%EC%9D%B4%EC%96%B8)
- [15961] 회전 초밥 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Gold/15961.%E2%80%85%ED%9A%8C%EC%A0%84%E2%80%85%EC%B4%88%EB%B0%A5)
- [11003] 최솟값 찾기 : deque를 사용한 슬라이딩 윈도우 문제 [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Platinum/11003.%E2%80%85%EC%B5%9C%EC%86%9F%EA%B0%92%E2%80%85%EC%B0%BE%EA%B8%B0)
- [1522] 문자열 교환 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1522.%E2%80%85%EB%AC%B8%EC%9E%90%EC%97%B4%E2%80%85%EA%B5%90%ED%99%98)

## SWEA
- [7510] 상원이의 연속 합 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/7510.%E2%80%85%EC%83%81%EC%9B%90%EC%9D%B4%EC%9D%98%E2%80%85%EC%97%B0%EC%86%8D%E2%80%85%ED%95%A9)
- [20728] 공평한 분배 2 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/20728.%E2%80%85%EA%B3%B5%ED%8F%89%ED%95%9C%E2%80%85%EB%B6%84%EB%B0%B0%E2%80%852)
- [19185] 육십갑자 : 투포인터 이용해 푸는 브루트포스 문제 [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/19185.%E2%80%85%EC%9C%A1%EC%8B%AD%EA%B0%91%EC%9E%90)
