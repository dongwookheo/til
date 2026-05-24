# void
- `void`는 “값이 없음”을 의미하는 타입
- 반환값이 없는 함수의 반환형으로 사용
- parameter가 없음을 명시할 때 `int main(void)`처럼 쓸 수 있음
- `void value;`처럼 void 변수는 만들 수 없음

## void*
- `void*`는 타입 정보 없이 주소를 담는 generic pointer
- `int*`, `float*` 같은 여러 타입의 주소를 담을 수 있음
- 다시 사용할 때는 원래 타입의 포인터로 형변환해야 함

```cpp
int i = 10;
void* ptr = &i;
int* int_ptr = static_cast<int*>(ptr);
```

## 주의
- `void*`는 주소만 담을 뿐, 그 주소에 있는 값을 어떤 타입으로 해석해야 하는지는 모름
- 따라서 `void*`를 직접 역참조할 수 없음
- 사용하려면 반드시 원래 타입으로 캐스팅해야 함
