# 고정 너비 정수 (Fixed-width Integer)
- 플랫폼마다 `int`, `short`, `long` 크기가 다를 수 있음
- C++11부터 `<cstdint>`에서 크기가 고정된 정수형 제공
- 예: `int16_t` = 정확히 16-bit signed integer = 2 byte
- 센서 패킷처럼 byte layout이 중요한 경우에 사용

## `int8_t` 주의
- `int8_t`는 `signed char`처럼 처리될 수 있음
- `std::cout << int8_t{65}`는 `65`가 아니라 `'A'`처럼 출력될 수 있음
- 숫자로 출력하려면 `static_cast<int>(value)`

## `int_fastN_t` / `int_leastN_t`
- `int_fast8_t`: 최소 8-bit 이상이면서 빠른 정수형
- `int_least64_t`: 최소 64-bit 이상인 정수형
- 정확한 packet layout이 필요하면 `int16_t`, `uint32_t`처럼 exact-width 타입 사용

## `std::size_t`
- 컨테이너 크기, 배열 크기, 인덱스에 쓰이는 unsigned 정수형
- `vector.size()`의 반환 타입
- `int`와 비교하면 signed/unsigned warning이 날 수 있음
