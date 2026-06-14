## 암시적 형변환
- 프로그래머가 직접 cast하지 않아도 C++ 규칙에 따라 자동 변환되는 것
- 예: `int → double`, `double → int`, `signed ↔ unsigned`
- 편리하지만 값 손실이나 예상 밖 결과가 생길 수 있음

## Numeric Promotion / Conversion
- Promotion: 더 넓은 타입으로 변환
  - 예: `float → double`, `char → int`
- Conversion: 타입 변환 중 정보 손실 가능성이 있는 변환
  - 예: `double → int`, `double → float`, `int → char`

## 명시적 형변환에서 주의할 부분
- C++ 스타일 명시적 형변환
- `std::`를 붙이지 않음

  ```cpp
  double d = 3.14;
  int i = static_cast<int>(d);
  ```
- signed / unsigned 주의
  - signed와 unsigned를 섞으면 unsigned 연산으로 처리될 수 있음
  - 음수가 큰 양수처럼 해석될 수 있음
  - 비교, 뺄셈, index 계산에서 특히 주의
