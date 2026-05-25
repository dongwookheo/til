## sizeof
- `sizeof`는 함수가 아니라 연산자
- 결과 단위는 byte
- 변수에는 괄호 없이 가능: `sizeof x`
- 타입에는 괄호 필요: `sizeof(int)`

## comma operator
- `(expr1, expr2)`는 `expr1`을 평가하고, 그 결과를 버린 뒤 `expr2`를 평가
- 전체 결과는 마지막 expression의 결과
- 예: `int z = (++x, ++y);` → `z`는 `++y`의 결과
- 단, 모든 쉼표가 comma operator는 아님
- 변수 선언과 함수 인자에서의 쉼표는 separator

## conditional operator
- 형태: `condition ? true_value : false_value`
- 간단한 조건 대입에 유용
- `const` 초기화와 함께 쓰기 좋음
- `<<`와 같이 쓸 때는 괄호로 묶는 것이 안전
