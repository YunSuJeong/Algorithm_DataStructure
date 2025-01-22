# Binary Search (이진탐색)

> **오름차순으로 정렬**된 수열에서 **중앙값**과 비교하여 특정 값을 찾아가는 알고리즘

## 구현
1. 배열의 중간값을 구한다.
2. 타겟과 중간값을 비교  
     2-1) 같으면 인덱스 리턴  
     2-2) 타겟이 작으면 왼쪽 배열에서 다시 탐색 (1번으로)  
     2-3) 타겟이 크면 오른쪽 배열에서 다시 탐색 (1번으로)  
3. 탐색이 완료될 때까지 반복

### Iterative 
```
// arr[n]과 target은 선언 되어있다고 가정
int low = 1, high = n, mid;
while( high < low ) {
  mid = (low+high)/2;
  if( target == arr[mid] )
    break;
  else if( target < arr[mid] )      
    high = mid-1;
  else                              
    low = mid+1;
}
```

### Recursive
```
binarySearch(int arr[], target, int low, int high) {
  if( high < low ) return -1;

  int mid = (low+high)/2;

  if( target == arr[mid] )
    return mid;
  else if( target < arr[mid] )      // 타겟이 중간값보다 작을 때 (중간값 기준으로 배열의 왼쪽)
    return binarySearch(arr[], target, low, mid-1);
  else                              // 타겟이 중간값보다 클 때 (중간값 기준으로 배열의 오른쪽)
    return binarySearch(arr[], target, mid+1, high);
}
```

## 예제
### 백준
- [1654] [랜선 자르기](https://www.acmicpc.net/problem/1654) : 🔎[소스 보기](https://github.com/YunSuJeong/BAEKJOON/blob/main/%EB%B0%B1%EC%A4%80/Silver/1654.%E2%80%85%EB%9E%9C%EC%84%A0%E2%80%85%EC%9E%90%EB%A5%B4%EA%B8%B0/%EB%9E%9C%EC%84%A0%E2%80%85%EC%9E%90%EB%A5%B4%EA%B8%B0.java)
- [1822] [차집합](https://www.acmicpc.net/problem/1822) : 🔎[소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/1822.%E2%80%85%EC%B0%A8%EC%A7%91%ED%95%A9)
- [2805] [나무 자르기](https://www.acmicpc.net/problem/2805) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/2805.%E2%80%85%EB%82%98%EB%AC%B4%E2%80%85%EC%9E%90%EB%A5%B4%EA%B8%B0)
