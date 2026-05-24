## '\n'
- 줄바꿈 문자만 출력
- 버퍼를 매번 비우지 않음
- 반복 출력에 유리함

## std::endl
- 줄바꿈 수행
- 추가로 flush 수행
- 매 반복마다 버퍼를 비워서 느릴 수 있음

> 아래 코드 결과:  
> \n time: 40 ms  
> std::endl time: 1027 ms  

```cpp
#include <iostream>
#include <fstream>
#include <chrono>

int main()
{
    constexpr int N = 1'000'000;

    // 1. '\n' 테스트
    {
        std::ofstream fout("newline_test.txt");

        std::chrono::time_point<std::chrono::steady_clock>start = std::chrono::high_resolution_clock::now();

        for (int i = 0; i < N; ++i)
        {
            fout << i << '\n';
        }

        std::chrono::time_point<std::chrono::steady_clock> end = std::chrono::high_resolution_clock::now();

        long long elapsed =
            std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();

        std::cout << "\\n time: " << elapsed << " ms" << std::endl;
    }

    // 2. std::endl 테스트
    {
        std::ofstream fout("endl_test.txt");

        std::chrono::time_point<std::chrono::steady_clock> start = std::chrono::high_resolution_clock::now();

        for (int i = 0; i < N; ++i)
        {
            fout << i << std::endl;
        }

        std::chrono::time_point<std::chrono::steady_clock> end = std::chrono::high_resolution_clock::now();

        long long elapsed =
            std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();

        std::cout << "std::endl time: " << elapsed << " ms" << std::endl;
    }

    return 0;
}
```
