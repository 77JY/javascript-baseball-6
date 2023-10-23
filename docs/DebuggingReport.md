# 문제점 및 해결 과정

## 1. 문제점 확인

### 1.1. 반복문 컨트롤 변수 이슈

- **상황**: 객체의 프로퍼티에 boolean 값을 할당하여 반복문의 컨트롤 변수로 사용했음.
- **문제**: 직접 테스트시 문제가 없었으나, Jest를 이용한 테스트에서는 통과하지 못함.

### 1.2. 출력 이슈

- **상황**: 첫번째 출력 이후 두번째 출력부터 문제가생김 정상작동의 경우 시작 메세지만 출력되며, 예외처리의 경우 undefined 로 끝나버림

## 2. 문제의 해결 과정

### 2.1. 반복문 컨트롤 변수 변경

- **해결 방법**: 객체의 프로퍼티 대신 일반 변수를 사용하여 반복문의 조건을 설정하니 문제가 해결됨. 
- **원인 파악**: 초기 실행 때 객체의 프로퍼티를 매번 초기화하고 새롭게 불러올 것이라 예상했으나, 실제로는 이전의 값을 계속 유지하고 있었음.

## 3. 결론

디버깅 시, 컨트롤 변수의 현재 상태를 콘솔로 출력하면 문제의 원인을 쉽게 파악할 수 있었다. 졸린 상태에서의 작업으로 인해 기본적인 디버깅 절차를 놓쳤다. 앞으로는 꼼꼼한 디버깅을 위해 상태를 정확히 확인하는 습관을 들여야겠다.