## const
- 초기화 이후 값을 바꿀 수 없게 함
- compile-time 값에도 쓸 수 있음
- runtime 값에도 쓸 수 있음

```cpp
const int a = 123;   // compile-time constant 가능
int input;
std::cin >> input;
const int b = input; // runtime constant
```

## constexpr
- 반드시 compile-time에 값이 결정되어야 함
- runtime 입력값으로 초기화할 수 없음

```cpp
constexpr int a = 123; // 가능

int input;
std::cin >> input;
constexpr int b = input; // 불가능
```

## 함수 매개변수의 const
- 함수 안에서 매개변수를 수정하지 못하게 막고 싶을 때 사용

```cpp
void printNumber(const int my_number)
{
    std::cout << my_number << std::endl;
}
