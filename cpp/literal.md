# 리터럴 표기
- `3.14`  : double literal
- `3.14f` : float literal
- `10u`   : unsigned integer literal
- `10L`   : long integer literal

## 진법 리터럴
- `012`    : 8진수 → decimal 10
- `0xF`    : 16진수 → decimal 15
- `0b1010` : 2진수 → decimal 10
> 숫자 앞에 실수로 `0`을 붙이면 8진수로 해석될 수 있으므로 주의

## digit separator
- C++14부터 숫자 중간에 `'` 사용 가능
- 가독성용이며 컴파일러는 무시
- 예: `1'000'000`, `0b1010'1100`
