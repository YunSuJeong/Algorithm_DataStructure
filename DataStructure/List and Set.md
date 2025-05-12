# List, Set

## List
> 데이터를 **순차적으로 저장하는 선형** 데이터 구조  
java에서는 Collection Framework의 일부이며, java.util.List 인터페이스로 제공된다.  

### 특징
  - 순서 유지(Order) : 요소가 추가된 순서로 저장됨, index로 접근 가능
  - 중복 허용(Duplication) : 동일한 값 여러번 저장 가능
  - 동적 크기(Dynamic Sizing) : 요소를 추가하면 자동으로 크기가 조정됨, 배열은 고정크기임!

### 주요 구현 클래스
1) ArrayList
  - 내부적으로 배열 기반으로 구현
  - 요소의 랜덤 접근 속도가 빠름 = O(1)
  - 중간에 요소를 삽입/삭제할 때는 느림 = O(n)
  - 읽기/검색이 많은 경우 적합
      
2) LinkedList
  - 내부적으로 이중 연결 리스트로 구현
  - 요소의 삽입/삭제가 빠름 = O(1), 특정 위치는 O(n)
  - 랜덤 접근이 느림 = O(n)
  - 삽입/삭제가 빈번한 경우 적합

### List vs Array(배열)
| 특징 | List | Array |
|---|---|---|
| 크기 | 동적으로 조절 가능 | 고정 크기 |
| 데이터 타입 | 객체 데이터만 저장 가능 | 객체와 기본 타입 모두 저장 가능 |
| 메서드 지원 | 다양한 유틸리티 메서드 제공 | 메서드가 없음 |
| 성능 | 삽입/삭제에 유연, 추가 비용 발생 | 직접 메모리 접근으로 빠름 |


## Set
> 중복을 허용하지 않는 컬렉션, **순서가 없는 요소**의 집합을 표현하는 인터페이스  
java.util.Collection를 상속한다.  
중복제거, 합/교집합 등의 작업에 적합

### 특징
  - 중복 허용 안함(No Duplicate) : 동일한 값을 여러번 저장X
  - 순서 없음(Unordered) : 저장된 요소의 순서 보장X. 특정 구현체에 따라 순서가 유지될 수는 있음. ex) LinkedHashSet
  - 효율적인 검색 : 요소 검색과 중복 확인 작업이 효율적

### 주요 구현 클래스
  1) HashSet  
    - 내부적으로 HashMap을 사용하여 구현.  
    - 요소의 순서를 보장하지 않음.  
    - 중복 제거와 검색 속도가 빠름 = O(1)  
    - 순서가 중요하지 않고, 빠른 삽입/검색이 필요한 경우에 적합  
     
  2) LinkedHashSet  
    - HashSet과 유사하지만, 요소의 삽입 순서를 유지.  
    - 메모리 사용량이 HashSet보다 약간 더 높음.  
    - 삽입 순서를 유지하면서 중복 제거를 원하는 경우에 적합  
     
  3) TreeSet  
    - 내부적으로 Red-Black Tree를 사용하여 구현.  
    - 요소가 정렬된 상태로 저장.  
    - 중복을 허용X, 순서를 유지하기 위해 더 많은 시간이 소요됨 = O(log n))  
    - 정렬된 데이터를 유지해야 하는 경우에 적합  

| 연산 |	HashSet |	LinkedHashSet |	TreeSet |
|---|---|---|---|
| 추가(Add) | O(1) |	O(1) | O(log n)
| 삭제(Remove) |	O(1) | O(1) |	O(log n)
| 검색(Contains) | O(1) | O(1) |	O(log n)
| 순회(Iteration) | O(n) |	O(n) | O(n)


### Set vs List
| 특징 | Set | List |
|---|---|---|
| 중복 여부 | X | O |
| 순서 | X | O |
| 접근 방식 | 인덱스로 접근X | 인덱스로 접근 |
| 주요 활용 | 중복 제거, 집합 연산 | 순서가 중요한 데이터 관리 |

## 예제
### 백준
- [26069] [붙임성 좋은 총총이](https://www.acmicpc.net/problem/26069) : [소스 보기](https://github.com/YunSuJeong/BAEKJOON/tree/main/%EB%B0%B1%EC%A4%80/Silver/26069.%E2%80%85%EB%B6%99%EC%9E%84%EC%84%B1%E2%80%85%EC%A2%8B%EC%9D%80%E2%80%85%EC%B4%9D%EC%B4%9D%EC%9D%B4)

### SWEA
- [2948] 문자열 교집합 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/2948.%E2%80%85%EB%AC%B8%EC%9E%90%EC%97%B4%E2%80%85%EA%B5%90%EC%A7%91%ED%95%A9)
