## `extern` 전역 상수 예시

- header에는 **선언**만 둔다
- cpp에는 **정의와 초기화**를 둔다
- 다른 파일에서는 header를 include해서 사용한다
- 여러 개의 파일에서 예문의 상수 변수를 불러와서 사용하더라고, **하나의 메모리에 할당된 상수**를 사용할 수 있다.

```cpp
// constants.hpp
#pragma once

namespace Constants
{
    extern const double pi;
    extern const double gravity;
}
```

```cpp
// constants.cpp
#include "constants.hpp"

namespace Constants
{
    extern const double pi = 3.141592653589793;
    extern const double gravity = 9.80665;
}
```

```cpp
// main.cpp
#include <iostream>
#include "constants.hpp"

int main()
{
    double radius = 2.0;
    double circumference = 2.0 * constants::pi * radius;

    std::cout << circumference << '\n';
    std::cout << constants::gravity << '\n';

    return 0;
}
```

## static at file scope
- 파일 scope에서 `static`을 붙이면 internal linkage
- 해당 `.cpp` 파일 안에서만 접근 가능
- 다른 `.cpp`에서 `extern`으로 접근 불가

```cpp
static int g_value = 10;  // 현재 파일 scope 내에서만 접근 가능

int main() {//...}
```
