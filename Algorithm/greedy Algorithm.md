# Greedy Algorithm (탐욕법)

> 최적의 해를 구하는 데에 사용되는 근사적인 방법으로,  
> **그 순간에 최적이라고 생각되는 것을 선택**해 나가는 방식으로 진행하여 **최종적인 해답에 도달**하는 방법이다.  
> 지역적으로 최적이면서 전역적으로 최적인 문제들에 적용가능하다.

## 적용 조건
### 1. 탐욕 선택 속성 (Greedy Choice Property)
각 단계에서 ‘최선의 선택’을 했을 때 전체 문제에 대한 최적해를 구할 수 있어야한다는 것!

### 2. 최적 부분 구조 (Optimal Substructure)
전체 문제의 최적해가 ‘부분 문제의 최적해로 구성’되어야한다는 뜻!

## 대표적인 그리디 문제
- 거스름돈 문제

## 예제
### 백준
- [25644] [최대 상승](https://www.acmicpc.net/problem/25644) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25644.%E2%80%85%EC%B5%9C%EB%8C%80%E2%80%85%EC%83%81%EC%8A%B9)
- [2891] [카약과 강풍](https://www.acmicpc.net/problem/2891) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2891.%E2%80%85%EC%B9%B4%EC%95%BD%EA%B3%BC%E2%80%85%EA%B0%95%ED%92%8D)
- [25214] [크림 파스타](https://www.acmicpc.net/problem/25214) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25214.%E2%80%85%ED%81%AC%EB%A6%BC%E2%80%85%ED%8C%8C%EC%8A%A4%ED%83%80)
- [25418] [정수 a를 k로 만들기](https://www.acmicpc.net/problem/25418) : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25418.%E2%80%85%EC%A0%95%EC%88%98%E2%80%85a%EB%A5%BC%E2%80%85k%EB%A1%9C%E2%80%85%EB%A7%8C%EB%93%A4%EA%B8%B0)

### SWEA
- [8338] 계산기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/8338.%E2%80%85%EA%B3%84%EC%82%B0%EA%B8%B0)

### 참고
- https://velog.io/@contea95/%ED%83%90%EC%9A%95%EB%B2%95%EA%B7%B8%EB%A6%AC%EB%94%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98
