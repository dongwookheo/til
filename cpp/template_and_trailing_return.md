# Template Function
- 매개변수와 반환형을 일반화해서 사용하고 싶을 때 사용
  ```cpp
  template <typename T, typename U>
  auto add(T x, U y)
  {
      return x + y;
  }
  ```

# Trailing Return Type
- 반환형을 함수 이름 뒤쪽에 쓰는 문법
- 단순 함수 가독성을 올려주는 정도의 효과가 있을 듯 (굳이 쓸 필요는 없다고 생각됨)
- template 코드에서는 매개변수를 먼저 선언한 뒤 반환형을 표현할 수 있어서 유용함
  ```cpp
  template <typename T, typename U>
  auto add(T x, U y) -> decltype(x + y)
  {
      return x + y;
  }
  ```
  - C++11: `decltype(x + y)`를 반환형에 쓰려면 trailing return type이 필요하다고 보면 됨
  - C++14 이후: 단순한 경우 `auto` 반환형 추론으로 생략 가능
  - 복잡한 template 코드에서는 여전히 trailing return type이 타입을 명확히 보여주는 데 유용함
