# 예외 사항 처리

## 1. 문제점 확인

### 1.1. 문자열 내 숫자 변환 이슈

- **상황**: 문자열 "1a2"를 `split().map(Number)` 처리하면 결과가 `[1, NaN, 2]`로 반환됨.
- **문제**: 예상했던 1~9 사이의 숫자 유효성 검사를 통과하는 것으로 생각했으나, `NaN` 값이 어떤 숫자와 비교해도 항상 `false` 반환을 몰랐음.

### 1.2. 테스트 케이스 이슈

- **상황**: 테스트 케이스 `["1a2", "135", "2"]`에 대하여 예외 처리 없이 통과하는 문제 발생.
- **원인**: `NaN` 값의 유무를 체크하지 않아 발생한 문제로 추정.

## 2. 문제의 해결 과정

### 2.1. `isNaN` 함수 사용

- **해결 방법**: 배열 내의 각 요소에 대해 `isNaN` 함수를 사용하여 `NaN` 값을 체크하고, 해당 값이 있는 경우 유효성 검사에서 제외하거나 오류를 반환하도록 처리.
- **결과**: 위의 해결 방법을 통해 테스트 케이스의 문제가 해결되었음.

## 3. 결론

예외 사항 처리 중 `NaN` 값의 유무를 체크하는 것을 놓쳤던 것이 원인이었다. 이를 `isNaN` 함수를 통해 해결하였으며, 앞으로는 이러한 기본적인 값을 체크하는 습관을 들여야겠다.