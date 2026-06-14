## std::string
- C++ built-in type이 아니라 표준 라이브러리의 class type
- 사용하려면 `<string>` include
- 문자열 리터럴은 `"Hello"`처럼 큰따옴표 사용

## string 입력
- `std::cin >> name;`
  - 공백 전까지만 입력
- `std::getline(std::cin, name);`
  - 줄바꿈 전까지 한 줄 전체 입력
 
## cin 다음 getline 주의
- `cin >>` 뒤에는 newline `'\n'`이 버퍼에 남을 수 있음
- 바로 `getline`을 쓰면 빈 문자열을 읽을 수 있음
- 해결:

  ```cpp
  std::cin.ignore(
      std::numeric_limits<std::streamsize>::max(),  // 개수
      '\n'                                          // 종료 문자
  );
  ```
