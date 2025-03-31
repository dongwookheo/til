## 0. GitHub Action 이란?
- 빌드, 테스트, 배포의 파이프라인을 자동화할 수 있는 CI/CD 플랫폼
    - CI (continuous integration)는 코드 변경 사항을 자동으로 빌드 및 테스트하여 통합 과정에서 발생할 수 있는 문제를 조기에 발견하는 개발 실천 방법
    - CD (continuous delivery)는 코드 변경 사항을 자동으로 배포하여 사용자에게 빠르고 안정적으로 전달하는 개발 실천 방법
**핵심 구성 요소**
- $\text{Workflows}$
    - 자동화된 프로세스를 지칭하며, 하나 이상의 job을 실행
    - `.github/workflows` 디렉토리에 YAML 파일로 정의
    - GitHub에서 호스팅하는 $\text{Runner}$라고 하는 가상 머신에서 수행된다.
    - $\text{Event}$, $\text{Schedule}$, $\text{Manual}$ 기반 트리거 가능
- $\text{Events}$
    - $\text{Workflow}$를 트리거하는 특정 활동
    - e.g. Pull request 생성, issue 오픈, commit push 등
- $\text{Jobs}$
    - 같은 $\text{Runner}$에서 실행되는 $\text{steps}$의 집합 (i.e. 수행할 task)
    - e.g. build, test, lint, deploy, …
    - 병렬 실행, 의존성 설정 가능, 순차적으로 실행되는 여러 steps로 구성
- $\text{Actions}$
    - 복잡하지만, 자주 반복되는 작업 단위를 캡슐화한 것
    - GitHub Marketplace에서 찾거나 직접 작성 가능
- $\text{Runners}$
    - $\text{Workflow}$가 트리거될 때, 실행되는 서버
    - GitHub 제공 서버: Windows, Ubuntu, macOS
    - 자체 호스팅 $\text{Runner}$ 구성 가능
 
---

## 1. 사용법
1. 프로젝트 디렉토리 밑에, `.github/workflows` 폴더를 만든다.
    1. 이 폴더 아래에 $\text{Workflow}$들이 저장된다.
2. YAML 형식으로 $\text{Workflow}$를 정의한다.
3. Repository의 변경사항을 commit → push 하면 자동으로 적용된다!

```YAML
name: 워크플로우 이름
run-name: 워크플로우 실행 이름 (선택사항)

on: # 트리거 이벤트
  push:
    branches: [main]
  pull_request:
    branches: [main]
  schedule:
    - cron: '0 0 * * *'  # 매일 자정에 실행
  workflow_dispatch:  # 수동 트리거
    inputs:
        item1:
            description: 'item1 사용 설명'
            required: true
            default: '기본값'

env:  # 전역 환경 변수
  SERVER: production

permissions: # GitHub 토큰 권한
  contents: read
  issues: write

jobs:
  my-job:  # 작업 ID
    name: 작업 이름
    runs-on: ubuntu-latest  # 실행 환경
    
    steps:  # 단계
      - name: 체크아웃
        uses: actions/checkout@v4  # Action
        
      - name: 명령어 실행
        run: echo "Hello, world!"
        
      - name: 환경 변수 사용
        env:
          LOCAL_VAR: 값
        run: echo $LOCAL_VAR
```
