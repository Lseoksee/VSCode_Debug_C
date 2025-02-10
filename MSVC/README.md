# VS Code C/C++ Debug With MSCV

VS Code 에서 Visual Studio의 컴파일러 MSCV(cl.exe)를 사용하여 디버깅 하는 템플릿

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

1. `Visual Studio 2022` 설치하기

2. 자기 `Visual Studio` 환경에 맞게 `.vscode/settings.json` 수정하기

    - 경로는 달라질 수 있으니 확인할 것

        - 달라질 경우 적절히 `tasks.json` 을 수정하자

    - MSVC 버전은 Visual Studio 업데이트시 바뀔 수 있음

    ```javascript
    {
    // MSCV 컴파일러 버전
    // C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC 폴더에서 확인
    "MSVC_VER": "14.41.34120",
    // 윈도우 Windows Kits 버전
    // C:\Program Files (x86)\Windows Kits\10\Include 폴더에서 확인
    "WINSDK_VER": "10.0.22621.0"
    }
    ```

3. VS Code에서 코드를 작성하고 디버깅 시작하기

### 라이브러리 추가

```text
"/I",
"해더파일 경로",
"/LIBPATH:라이브러기 경로"
```

-   요구되는 라이브러리 추가될때 마다 `tasks.json` 의 `args` 쪽에 위 구문을 추가한다
-   `cl.exe` 가 링커 작업을 할때 적절히 라이브러리를 포함 하는 작업을 해야 한다
- `/LIBPATH` 에 경우 `/link` 옵션 뒤에 들어가야 한다
