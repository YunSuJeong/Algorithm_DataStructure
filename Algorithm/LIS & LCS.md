# LIS 와 LCS

## 최장 증가 부분 수열 (LIS, Longest Increasing Subsequence)
### LIS를 알아보기 전에 알아야할 개념.!
**부분 수열(Subsquence)란 뭘까?**  
- 부분 수열이란 원래 배열에서 일부 원소를 제거하면서도 원래 순서는 유지하는 것이다.
- 예) [10, 20, 30]는 [10, 22, 9, 33, 21, 50]의 부분 수열

### LIS란?
말 그대로 주어진 수열에서 **가장 긴 증가하는 부분 수열**을 찾는 문제이다.  
부분 수열이므로 원소의 순서를 유지해야하니까 원소를 재배열한다거나 하는 문제는 아닌거다.  
아래의 최장 증가 부분 수열을 생각해보자.  

[10, 22, 33, 50, 60, 80]이므로 길이는 6이다.
```java
  arr = [10, 22, 9, 33, 21, 50, 41, 60, 80]
```

### 어디에 사용될까?
1. 최적 경로 찾기  
예를 들어, 어떤 도시에서 출발하여 시간이 증가하는 방향으로 가장 긴 여행 경로를 찾을 때 사용할 수 있어.

2. LCS(Longest Common Subsequence, 최장 공통 부분 수열)와의 관계  
LIS 알고리즘은 LCS와도 연관이 있다. LCS 문제에서 두 번째 수열을 "정렬된 상태"로 바꾸면 LIS 문제가 되기도 한다.  
(아직 LIS, LCS 문제들을 많이 접해보지 않아 이해가 가진 않는다.)

### DP로 구현하기
구현은 기본적으로 **DP를 이용**한다.  

**왜 DP로 풀어야 할까?** 
> 탐욕법적 고민 : "앞에서부터 순차적으로 보면서, 현재 값보다 큰 숫자를 만나면 그냥 이어붙이면 되지 않을까?"
```java
  arr = [3, 10, 2, 1, 4, 6, 20]
```
맨 앞부터 그리디하게 최장 증가 부분 수열을 구하면, 3 → 10 → 20이므로 길이는 3이다.  
그러나 최장 증가 부분 수열은 3 → 4 → 6 → 10으로 사실 4다.  
10보다 작은 수들을 건너뛰게 되면서 재대로 답을 구할 수 없게 된다.

즉, 이 문제는 **미래에 더 좋은 선택이 올 수 있으므로 greedy(탐욕법)로 해결할 수 없다!**

**과거의 모든 가능한 경우를 고려해야 하기 때문에** **DP(동적 계획법)**이 필요하다!

위의 케이스로 설명하자면, 원소 6까지의 LIS를 구하려면 고려해야하는 경우는 아래 4가지일 것이다.  
[3 → 6], [2 → 6], [1 → 6], [4`(얘는 1→4이므로 LIS는 2인 상태일 것이다.)` → 6]  
현재 숫자 6보다 작은 수들의 LIS중 가장 큰 값이 필요하기 때문에, 과거의 모든 가능한 경우를 고려해야한다고 설명했던 것.!

**📌 알고리즘 동작 방식**  
> **각 위치에서 끝나는 LIS의 길이를 저장**하는 dp 배열을 활용하는 것이 포인트!
1. dp[i] = i번째 원소를 마지막 원소로 하는 LIS의 길이라고 정의한다.  
2. 초기값 세팅 : 모든 dp[i] = 1 (**자기 자신** 하나만 포함하는 경우)  
3. 이전 원소들과 비교하며 최적의 LIS 값을 찾는다.  
  i번째 원소에서 끝나는 LIS는 i보다 앞에 있는 모든 j (0 ≤ j < i)에 대해 arr[j] < arr[i]인 경우 중 최대LIS를 고려  
  arr[j] < arr[i]라면 arr[i]를 arr[j] 뒤에 붙일 수 있으므로, dp[i] = max(dp[i], dp[j] + 1)을 갱신  
  즉, 앞에서 LIS가 길었던 곳을 활용해서 dp[i] 값을 최대로 만들어간다!
4. dp 배열의 최댓값 = LIS의 길이
   
```java
import java.util.*;

public class LIS_DP {
    public static int lis(int[] arr) {
        int n = arr.length;
        int[] dp = new int[n];
        Arrays.fill(dp, 1);         // 모든 원소의 LIS 기본값은 1

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i; j++) {     // i 이전의 원소들과 비교
                if (arr[j] < arr[i]) {        // 증가하는 순서라면
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
        }

        // dp 배열에서 최댓값 찾기
        int maxLength = 0;
        for (int len : dp) {
            maxLength = Math.max(maxLength, len);
        }
        return maxLength;
    }

    public static void main(String[] args) {
        int[] arr = {10, 22, 9, 33, 21, 50, 41, 60, 80};
        System.out.println("LIS 길이: " + lis(arr));     // 결과: 6
    }
}
```

**시간복잡도 분석**  
- 이중 루프를 이용하므로 **O(N²)**
- 작은 입력에서는 충분하지만, N ≥ 10,000 일 때는 더 빠른 알고리즘이 필요하다. (그치만 아직 쪼렙이라 그런 문제들을 만나보지 못한 관계로,, 추후에 정리 예정이다.)

## LCS

## LCS

## 예제
### 백준
- [22857] [가장 긴 짝수 연속한 부분 수열 (small)](https://www.acmicpc.net/problem/22857) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/22857.%E2%80%85%EA%B0%80%EC%9E%A5%E2%80%85%EA%B8%B4%E2%80%85%EC%A7%9D%EC%88%98%E2%80%85%EC%97%B0%EC%86%8D%ED%95%9C%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4%E2%80%85%EF%BC%88small%EF%BC%89)
- [17216] [가장 큰 감소 부분 수열](https://www.acmicpc.net/problem/17216) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/17216.%E2%80%85%EA%B0%80%EC%9E%A5%E2%80%85%ED%81%B0%E2%80%85%EA%B0%90%EC%86%8C%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4)
- [11053] [가장 긴 증가하는 부분 수열](https://www.acmicpc.net/problem/11053) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11053.%E2%80%85%EA%B0%80%EC%9E%A5%E2%80%85%EA%B8%B4%E2%80%85%EC%A6%9D%EA%B0%80%ED%95%98%EB%8A%94%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4)
- [18353] [병사 배치하기](https://www.acmicpc.net/problem/18353) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/18353.%E2%80%85%EB%B3%91%EC%82%AC%E2%80%85%EB%B0%B0%EC%B9%98%ED%95%98%EA%B8%B0)
- [1965] [상자넣기](https://www.acmicpc.net/problem/1965) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1965.%E2%80%85%EC%83%81%EC%9E%90%EB%84%A3%EA%B8%B0)
- [11722] [가장 긴 감소하는 부분 수열](https://www.acmicpc.net/problem/11722) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/11722.%E2%80%85%EA%B0%80%EC%9E%A5%E2%80%85%EA%B8%B4%E2%80%85%EA%B0%90%EC%86%8C%ED%95%98%EB%8A%94%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4)

### SWEA
- [3304] [최장 공통 부분 수열](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWBOHEx66kIDFAWr&categoryId=AWBOHEx66kIDFAWr&categoryType=CODE&problemTitle=3304&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=&pageSize=10&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/3304.%E2%80%85%EC%B5%9C%EC%9E%A5%E2%80%85%EA%B3%B5%ED%86%B5%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4)
- [3307] [최장 증가 부분 수열](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWBOKg-a6l0DFAWr&categoryId=AWBOKg-a6l0DFAWr&categoryType=CODE&problemTitle=3307&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=&pageSize=10&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/3307.%E2%80%85%EC%B5%9C%EC%9E%A5%E2%80%85%EC%A6%9D%EA%B0%80%E2%80%85%EB%B6%80%EB%B6%84%E2%80%85%EC%88%98%EC%97%B4)
- [6190] [정곤이의 단조 증가하는 수](https://swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AWcPjEuKAFgDFAU4&categoryId=AWcPjEuKAFgDFAU4&categoryType=CODE&problemTitle=6190&orderBy=FIRST_REG_DATETIME&selectCodeLang=ALL&select-1=&pageSize=10&pageIndex=1) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/6190.%E2%80%85%EC%A0%95%EA%B3%A4%EC%9D%B4%EC%9D%98%E2%80%85%EB%8B%A8%EC%A1%B0%E2%80%85%EC%A6%9D%EA%B0%80%ED%95%98%EB%8A%94%E2%80%85%EC%88%98)

## 참고
- https://nayoungs.tistory.com/entry/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-LCSLongest-Common-Subsequence-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%EC%9D%B4%EB%9E%80
