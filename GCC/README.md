# VS Code C/C++ Debug With GCC

VS Code 에서 GCC 컴파일러를 사용하여 디버깅 하는 템플릿

윈도우 & 리눅스 상호 운용 가능

## 사용법

### default / with-dir 폴더 차이점

-   `main`:

    작업 폴더와 상관 없이 빌드 파일은 `bin` 폴더에 생성됨

    만약 다른 폴더에서 동일한 파일 명으로 작업후 빌드 시 동일한 이름에 실행 파일로 생성이 되는데 기존에 있던 실행 파일에 덮어써짐

    -   예를들어 `src/main.c`, `src/src2/main.c` 는 빌드 시 동일하게 `bin/main.exe` 로 저장된다

    일반적인 디버깅에는 상관 없지만 좀 찝찝할 수 있음

-   `with_dir`:

    작업 폴더와 `bin` 폴더에 구조를 동일하게 맞춤

    -   예를들어 `src` 폴더에 작업한다면 `bin/src` 폴더에 빌드파일이 생성이 됨

    동일한 폴더 구조로 실행파일명이 같더라도 폴더가 다르니 겹치는 문제 없음

    대신 폴더를 만드는 전처리 과정이 들어가서 빌드시간이 좀 더 걸림

### 디버깅 가이드

#### 윈도우

1. [mingw-w64 설치](https://github.com/niXman/mingw-builds-binaries/releases)

2. 설치된 `<mingw 경로>/bin`에 환경변수 설정하기


#### 리눅스

```bash
sudo apt install gcc gdb
```

### 라이브러리 추가

```text
"-I<해더파일 경로>",
"-L<라이브러리 경로>",
"-l<라이브러리 이름>",
```

-   요구되는 라이브러리 추가될때 마다 `tasks.json` 의 `args` 쪽에 위 구문을 추가한다
