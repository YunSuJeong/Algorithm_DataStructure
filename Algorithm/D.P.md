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
- [19947] [투자의 귀재 배주형](https://www.acmicpc.net/problem/19947) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/19947.%E2%80%85%ED%88%AC%EC%9E%90%EC%9D%98%E2%80%85%EA%B7%80%EC%9E%AC%E2%80%85%EB%B0%B0%EC%A3%BC%ED%98%95)
- [14606] [피자 (Small)](https://www.acmicpc.net/problem/14606) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14606.%E2%80%85%ED%94%BC%EC%9E%90%E2%80%85%EF%BC%88Small%EF%BC%89)
- [9625] [BABBA](https://www.acmicpc.net/problem/9625) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/9625.%E2%80%85BABBA)
- [32981] [찐 Even Number](https://www.acmicpc.net/problem/32981) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/32981.%E2%80%85%EC%B0%90%E2%80%85Even%E2%80%85Number)
- [1149] [RGB거리](https://www.acmicpc.net/problem/1149) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1149.%E2%80%85RGB%EA%B1%B0%EB%A6%AC)
- [15489] [파스칼 삼각형](https://www.acmicpc.net/problem/15489) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/15489.%E2%80%85%ED%8C%8C%EC%8A%A4%EC%B9%BC%E2%80%85%EC%82%BC%EA%B0%81%ED%98%95)
- [2491] [수열](https://www.acmicpc.net/problem/2491) : [소스보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2491.%E2%80%85%EC%88%98%EC%97%B4)
- [9657] [돌 게임 3](https://www.acmicpc.net/problem/9657) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/9657.%E2%80%85%EB%8F%8C%E2%80%85%EA%B2%8C%EC%9E%84%E2%80%853)
- [14501] [퇴사](https://www.acmicpc.net/problem/14501) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14501.%E2%80%85%ED%87%B4%EC%82%AC)
- [8394] [악수](https://www.acmicpc.net/problem/8394) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/8394.%E2%80%85%EC%95%85%EC%88%98)
- [25706] [자전거 묘기](https://www.acmicpc.net/problem/25706) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25706.%E2%80%85%EC%9E%90%EC%A0%84%EA%B1%B0%E2%80%85%EB%AC%98%EA%B8%B0)
- [2670] [연속부분최대곱](https://www.acmicpc.net/problem/2670) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2670.%E2%80%85%EC%97%B0%EC%86%8D%EB%B6%80%EB%B6%84%EC%B5%9C%EB%8C%80%EA%B3%B1)
- [14231] [박스 포장](https://www.acmicpc.net/problem/14231) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14231.%E2%80%85%EB%B0%95%EC%8A%A4%E2%80%85%ED%8F%AC%EC%9E%A5)
- [23560] [약](https://www.acmicpc.net/problem/23560) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/23560.%E2%80%85%EC%95%BD)
- [21555] [빛의 돌 옮기기](https://www.acmicpc.net/problem/21555) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/21555.%E2%80%85%EB%B9%9B%EC%9D%98%E2%80%85%EB%8F%8C%E2%80%85%EC%98%AE%EA%B8%B0%EA%B8%B0)
- [28450] [컨벤 데드가 하고싶어요](https://www.acmicpc.net/problem/28450) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/28450.%E2%80%85%EC%BB%A8%EB%B2%A4%E2%80%85%EB%8D%B0%EB%93%9C%EA%B0%80%E2%80%85%ED%95%98%EA%B3%A0%EC%8B%B6%EC%96%B4%EC%9A%94)
- [22971] [증가하는 부분 수열의 개수](https://www.acmicpc.net/problem/22971) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/22971.%E2%80%85%EC%A6%9D%EA%B0%80%ED%95%98%EB%8A%94%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4%EC%9D%98%E2%80%85%EA%B0%9C%EC%88%98)
- [31670] [특별한 마법 공격](https://www.acmicpc.net/problem/31670) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/31670.%E2%80%85%ED%8A%B9%EB%B3%84%ED%95%9C%E2%80%85%EB%A7%88%EB%B2%95%E2%80%85%EA%B3%B5%EA%B2%A9)
- [22114] [창영이와 점프](https://www.acmicpc.net/problem/22114) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/22114.%E2%80%85%EC%B0%BD%EC%98%81%EC%9D%B4%EC%99%80%E2%80%85%EC%A0%90%ED%94%84)
- [18249] [욱제가 풀어야 하는 문제](https://www.acmicpc.net/problem/18249) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/18249.%E2%80%85%EC%9A%B1%EC%A0%9C%EA%B0%80%E2%80%85%ED%92%80%EC%96%B4%EC%95%BC%E2%80%85%ED%95%98%EB%8A%94%E2%80%85%EB%AC%B8%EC%A0%9C)
- [13270] [피보나치 치킨](https://www.acmicpc.net/problem/13270) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/13270.%E2%80%85%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98%E2%80%85%EC%B9%98%ED%82%A8)
- [20162] [간식 파티](https://www.acmicpc.net/problem/20162) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/20162.%E2%80%85%EA%B0%84%EC%8B%9D%E2%80%85%ED%8C%8C%ED%8B%B0)
- [20152] [Game Addiction](https://www.acmicpc.net/problem/20152) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/20152.%E2%80%85Game%E2%80%85Addiction)
- [19622] [회의실 배정 3](https://www.acmicpc.net/problem/19622) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/19622.%E2%80%85%ED%9A%8C%EC%9D%98%EC%8B%A4%E2%80%85%EB%B0%B0%EC%A0%95%E2%80%853)
- [17291] [새끼치기](https://www.acmicpc.net/problem/17291) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/17291.%E2%80%85%EC%83%88%EB%81%BC%EC%B9%98%EA%B8%B0)
- [11867] 박스 나누기 게임 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11867.%E2%80%85%EB%B0%95%EC%8A%A4%E2%80%85%EB%82%98%EB%88%84%EA%B8%B0%E2%80%85%EA%B2%8C%EC%9E%84)
- [17271] 리그 오브 레전설 (Small) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/17271.%E2%80%85%EB%A6%AC%EA%B7%B8%E2%80%85%EC%98%A4%EB%B8%8C%E2%80%85%EB%A0%88%EC%A0%84%EC%84%A4%E2%80%85%EF%BC%88Small%EF%BC%89)
- [17213] 과일 서리 : 중복 조합 문제 [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/17213.%E2%80%85%EA%B3%BC%EC%9D%BC%E2%80%85%EC%84%9C%EB%A6%AC)
- [19622] 회의실 배정 3 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/19622.%E2%80%85%ED%9A%8C%EC%9D%98%EC%8B%A4%E2%80%85%EB%B0%B0%EC%A0%95%E2%80%853)
- [11060] 점프 점프 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11060.%E2%80%85%EC%A0%90%ED%94%84%E2%80%85%EC%A0%90%ED%94%84)
- [4097] 수익 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/4097.%E2%80%85%EC%88%98%EC%9D%B5)
- [11568] 민균이의 계략 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11568.%E2%80%85%EB%AF%BC%EA%B7%A0%EC%9D%B4%EC%9D%98%E2%80%85%EA%B3%84%EB%9E%B5)
- [14430] 자원 캐기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14430.%E2%80%85%EC%9E%90%EC%9B%90%E2%80%85%EC%BA%90%EA%B8%B0)
- [1793] 타일링 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1793.%E2%80%85%ED%83%80%EC%9D%BC%EB%A7%81)
- [9658] 돌 게임 4 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/9658.%E2%80%85%EB%8F%8C%E2%80%85%EA%B2%8C%EC%9E%84%E2%80%854)
- [1535] 안녕 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1535.%E2%80%85%EC%95%88%EB%85%95)
- [11048] 이동하기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11048.%E2%80%85%EC%9D%B4%EB%8F%99%ED%95%98%EA%B8%B0)
- [1679] 숫자놀이 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1679.%E2%80%85%EC%88%AB%EC%9E%90%EB%86%80%EC%9D%B4)
- [32931] 자석 놀이 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/32931.%E2%80%85%EC%9E%90%EC%84%9D%E2%80%85%EB%86%80%EC%9D%B4)
- [32202] 풀이 전달 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/32202.%E2%80%85%ED%92%80%EC%9D%B4%E2%80%85%EC%A0%84%EB%8B%AC)
- [1697] 숨바꼭질 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1697.%E2%80%85%EC%88%A8%EB%B0%94%EA%BC%AD%EC%A7%88)
- [2156] 포도주 시식 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2156.%E2%80%85%ED%8F%AC%EB%8F%84%EC%A3%BC%E2%80%85%EC%8B%9C%EC%8B%9D)
- [11726] 2×n 타일링 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11726.%E2%80%852%C3%97n%E2%80%85%ED%83%80%EC%9D%BC%EB%A7%81)
- [7579] 앱 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Gold/7579.%E2%80%85%EC%95%B1)
- [12865] 평범한 배낭 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Gold/12865.%E2%80%85%ED%8F%89%EB%B2%94%ED%95%9C%E2%80%85%EB%B0%B0%EB%82%AD)
- [33677] 푸앙이와 콩나무 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/33677.%E2%80%85%ED%91%B8%EC%95%99%EC%9D%B4%EC%99%80%E2%80%85%EC%BD%A9%EB%82%98%EB%AC%B4)
- [27446] 랩실에서 잘 자요 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/27446.%E2%80%85%EB%9E%A9%EC%8B%A4%EC%97%90%EC%84%9C%E2%80%85%EC%9E%98%E2%80%85%EC%9E%90%EC%9A%94)
- [3976] 역습 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/3976.%E2%80%85%EC%97%AD%EC%8A%B5)
- [10164] 격자상의 경로 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/10164.%E2%80%85%EA%B2%A9%EC%9E%90%EC%83%81%EC%9D%98%E2%80%85%EA%B2%BD%EB%A1%9C)
- [2302] 극장 좌석 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2302.%E2%80%85%EA%B7%B9%EC%9E%A5%E2%80%85%EC%A2%8C%EC%84%9D)
- [21600] 계단 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/21600.%E2%80%85%EA%B3%84%EB%8B%A8)
- [14613] 너의 티어는? : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/14613.%E2%80%85%EB%84%88%EC%9D%98%E2%80%85%ED%8B%B0%EC%96%B4%EB%8A%94%EF%BC%9F)
- [1932] 정수 삼각형 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1932.%E2%80%85%EC%A0%95%EC%88%98%E2%80%85%EC%82%BC%EA%B0%81%ED%98%95)
- [32175] 컵 쌓기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/32175.%E2%80%85%EC%BB%B5%E2%80%85%EC%8C%93%EA%B8%B0)
- [15993] 1, 2, 3 더하기 8 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/15993.%E2%80%851%EF%BC%8C%E2%80%852%EF%BC%8C%E2%80%853%E2%80%85%EB%8D%94%ED%95%98%EA%B8%B0%E2%80%858)
- [2705] 팰린드롬 파티션 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2705.%E2%80%85%ED%8C%B0%EB%A6%B0%EB%93%9C%EB%A1%AC%E2%80%85%ED%8C%8C%ED%8B%B0%EC%85%98)
- [2780] 비밀번호 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2780.%E2%80%85%EB%B9%84%EB%B0%80%EB%B2%88%ED%98%B8)
- [31910] 이진수 격자 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/31910.%E2%80%85%EC%9D%B4%EC%A7%84%EC%88%98%E2%80%85%EA%B2%A9%EC%9E%90)
- [10844] 쉬운 계단 수 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/10844.%E2%80%85%EC%89%AC%EC%9A%B4%E2%80%85%EA%B3%84%EB%8B%A8%E2%80%85%EC%88%98)
- [11052] 카드 구매하기 : [소스 보기](http://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11052.%E2%80%85%EC%B9%B4%EB%93%9C%E2%80%85%EA%B5%AC%EB%A7%A4%ED%95%98%EA%B8%B0)
- [11660] 구간 합 구하기 5 : 누적합 이용 DP [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11660.%E2%80%85%EA%B5%AC%EA%B0%84%E2%80%85%ED%95%A9%E2%80%85%EA%B5%AC%ED%95%98%EA%B8%B0%E2%80%855)
- [1309] 동물원 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1309.%E2%80%85%EB%8F%99%EB%AC%BC%EC%9B%90)

### SWEA
- [5215] [햄버거 다이어트](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AWT-lPB6dHUDFAVT&categoryId=AWT-lPB6dHUDFAVT&categoryType=CODE&problemTitle=5215&orderBy=RECOMMEND_COUNT&selectCodeLang=ALL&select-1=3&pageSize=30&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/5215.%E2%80%85%ED%96%84%EB%B2%84%EA%B1%B0%E2%80%85%EB%8B%A4%EC%9D%B4%EC%96%B4%ED%8A%B8)
- [3307] [최장 증가 부분 수열](https://swexpertacademy.com/main/code/problem/problemDetail.do?problemLevel=3&contestProbId=AWBOKg-a6l0DFAWr&categoryId=AWBOKg-a6l0DFAWr&categoryType=CODE&problemTitle=&orderBy=RECOMMEND_COUNT&selectCodeLang=ALL&select-1=3&pageSize=30&pageIndex=2) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/3307.%E2%80%85%EC%B5%9C%EC%9E%A5%E2%80%85%EC%A6%9D%EA%B0%80%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4)
- [22574] [높은 곳으로](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AZIieDaq5AEDFAXd&categoryId=AZIieDaq5AEDFAXd&categoryType=CODE&problemTitle=22574&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=&pageSize=10&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/22574.%E2%80%85%EB%86%92%EC%9D%80%E2%80%85%EA%B3%B3%EC%9C%BC%EB%A1%9C)
- [21131] 행렬정렬 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/21131.%E2%80%85%ED%96%89%EB%A0%AC%EC%A0%95%EB%A0%AC)
- [4466] 최대 성적표 만들기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/4466.%E2%80%85%EC%B5%9C%EB%8C%80%E2%80%85%EC%84%B1%EC%A0%81%ED%91%9C%E2%80%85%EB%A7%8C%EB%93%A4%EA%B8%B0)
- [1859] 백만 장자 프로젝트 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D2/1859.%E2%80%85%EB%B0%B1%EB%A7%8C%E2%80%85%EC%9E%A5%EC%9E%90%E2%80%85%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8)
- [5642] [Professional] 합 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/5642.%E2%80%85%EF%BC%BBProfessional%EF%BC%BD%E2%80%85%ED%95%A9)
- [22039] 피보나치 수 분배 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/22039.%E2%80%85%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98%E2%80%85%EC%88%98%E2%80%85%EB%B6%84%EB%B0%B0)

[참고] https://hongjw1938.tistory.com/47

      
