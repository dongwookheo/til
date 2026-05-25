# Bit Flag 조작 패턴

- 각 bit를 하나의 on/off flag처럼 사용
- `1 << n`으로 n번째 bit에 해당하는 mask를 만든다

```cpp
constexpr unsigned char opt0 = 1 << 0; // 0000'0001
constexpr unsigned char opt1 = 1 << 1; // 0000'0010
constexpr unsigned char opt2 = 1 << 2; // 0000'0100
constexpr unsigned char opt3 = 1 << 3; // 0000'1000
```

- bit 켜기: `|= mask`
  ```cpp
  items_flag |= opt3;
  ```
- bit 끄기: `&= ~mask`
  ```cpp
  items_flag &= ~opt3;
  ```
- bit 확인: `& mask`
  ```cpp
  if (items_flag & opt3)
  {
    // opt3 bit is on
  }
  ```
- bit 토글: `^= mask`
  ```cpp
  items_flag ^= opt3;
  ```
- 여러 bit 동시에 켜기
  ```cpp
  items_flag |= (opt2 | opt3);
  ```

# RGB Bit Mask 추출

- `0xRRGGBB` 형식에서는 각 색상이 1 byte씩 들어 있음
- `& mask`로 원하는 byte만 남기고, `>>`로 오른쪽 끝으로 정렬

```cpp
unsigned int color = 0xDAA520;
```
- RGB/BGR/RGBA/ARGB 순서는 포맷 약속이므로 반드시 확인

unsigned char red   = static_cast<unsigned char>((color & 0xFF0000) >> 16);
unsigned char green = static_cast<unsigned char>((color & 0x00FF00) >> 8);
unsigned char blue  = static_cast<unsigned char>( color & 0x0000FF);
```
