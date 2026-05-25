## Short-circuit Evaluation
- `&&`: 왼쪽이 false이면 오른쪽을 평가하지 않을 수 있음
- `||`: 왼쪽이 true이면 오른쪽을 평가하지 않을 수 있음
- 따라서 오른쪽에 `y++`, 함수 호출, 상태 변경 코드가 있으면 주의

```cpp
int x = 2;
int y = 2;

if (x == 1 && y++ == 2) {}

std::cout << y; // 2
```

## 논리 XOR
- C++에는 논리 XOR 전용 `^^` 없음
- `^`는 bitwise XOR
- bool 값에 대해서는 `x != y`를 XOR처럼 사용할 수 있음

```cpp
bool xor_result = (x != y);
```

## De Morgan 법칙
- `!(x && y)` → `!x || !y`
- `!(x || y)` → `!x && !y`
