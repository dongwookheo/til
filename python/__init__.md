## `__init__.py` 란? 
- **패키지 초기화 스크립트 (package initialization script)** 로, 해당 디렉토리가 **Python 패키지임을 명시**하고 초기화 코드를 실행할 수 있도록 하는 파일이다.
- 로깅 설정, 경로 추가, 환경 변수 설정, 라이브러리 초기화 등에 활용될 수 있다.
- 아래의 예시에서, `__all__`에 명시된 클래스만, 와일드 카드 import로 import 할 수 있다. (`from something import *`)

```Python
# __init__.py 예시
from .ekf import EKFLocalizer
from .graph_optimizer import GraphOptimizer

_hidden_func = lambda: print("I'm hidden")
__all__ = ['EKFLocalizer']
print("Initialized my_localizer")
```
