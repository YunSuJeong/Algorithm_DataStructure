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
- [25644] 최대 상승 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25644.%E2%80%85%EC%B5%9C%EB%8C%80%E2%80%85%EC%83%81%EC%8A%B9)
- [2891] 카약과 강풍 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2891.%E2%80%85%EC%B9%B4%EC%95%BD%EA%B3%BC%E2%80%85%EA%B0%95%ED%92%8D)
- [25214] 크림 파스타 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25214.%E2%80%85%ED%81%AC%EB%A6%BC%E2%80%85%ED%8C%8C%EC%8A%A4%ED%83%80)
- [25418] 정수 a를 k로 만들기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25418.%E2%80%85%EC%A0%95%EC%88%98%E2%80%85a%EB%A5%BC%E2%80%85k%EB%A1%9C%E2%80%85%EB%A7%8C%EB%93%A4%EA%B8%B0)
- [25215] 타이핑 : ★★ [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/25215.%E2%80%85%ED%83%80%EC%9D%B4%ED%95%91)
- [32200] 항해 : A의 최대이면서 B의 최소값을 구하는 문제 [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/32200.%E2%80%85%ED%95%AD%ED%95%B4)
- [2057] 팩토리얼 분해 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2057.%E2%80%85%ED%8C%A9%ED%86%A0%EB%A6%AC%EC%96%BC%E2%80%85%EB%B6%84%ED%95%B4)
- [19941] 햄버거 분배 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/19941.%E2%80%85%ED%96%84%EB%B2%84%EA%B1%B0%E2%80%85%EB%B6%84%EB%B0%B0)
- [2217] 로프 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2217.%E2%80%85%EB%A1%9C%ED%94%84)
- [1049] 기타줄 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1049.%E2%80%85%EA%B8%B0%ED%83%80%EC%A4%84)
- [2847] 게임을 만든 동준이 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2847.%E2%80%85%EA%B2%8C%EC%9E%84%EC%9D%84%E2%80%85%EB%A7%8C%EB%93%A0%E2%80%85%EB%8F%99%EC%A4%80%EC%9D%B4)
- [1448] 삼각형 만들기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1448.%E2%80%85%EC%82%BC%EA%B0%81%ED%98%95%E2%80%85%EB%A7%8C%EB%93%A4%EA%B8%B0)
- [1449] 수리공 항승 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1449.%E2%80%85%EC%88%98%EB%A6%AC%EA%B3%B5%E2%80%85%ED%95%AD%EC%8A%B9)
- [1783] 병든 나이트 : ★★ [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/1783.%E2%80%85%EB%B3%91%EB%93%A0%E2%80%85%EB%82%98%EC%9D%B4%ED%8A%B8)
- [2012] 등수 매기기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/%EB%B0%B1%EC%A4%80/Silver/2012.%E2%80%85%EB%93%B1%EC%88%98%E2%80%85%EB%A7%A4%EA%B8%B0%EA%B8%B0)
  
### SWEA
- [8338] 계산기 : [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/8338.%E2%80%85%EA%B3%84%EC%82%B0%EA%B8%B0)
- [5162] 두가지 빵의 딜레마 : 최대 빵 개수 구하는 문제 [소스 보기](https://github.com/YunSuJeong/Coding-Test/tree/main/SWEA/D3/5162.%E2%80%85%EB%91%90%EA%B0%80%EC%A7%80%E2%80%85%EB%B9%B5%EC%9D%98%E2%80%85%EB%94%9C%EB%A0%88%EB%A7%88)

### 참고
- https://velog.io/@contea95/%ED%83%90%EC%9A%95%EB%B2%95%EA%B7%B8%EB%A6%AC%EB%94%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98
