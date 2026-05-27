# Namespace
- 이름 충돌을 줄이기 위한 이름 공간
- `::`는 scope resolution operator
- 어느 namespace의 이름을 사용할지 명확히 지정

```cpp
namespace Work1 { void doSomething() {} }
namespace Work2 { void doSomething() {} }

Work1::doSomething();
Work2::doSomething();
```

## C++17 Nested Namespace
- 중첩 namespace를 한 줄로 줄여 쓸 수 있음

```cpp
namespace A::B::C
{
    void func() {}
}
```
