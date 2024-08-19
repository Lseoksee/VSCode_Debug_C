# VS Code C/C++ Debug With MSCV

VS Code 에서 GCC 가 아닌 Visual Studio의 컴파일러 MSCV(cl.exe)를 사용하여 디버깅 하는 템플릿

## 사용법

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
"라이브러리경로",
```

-   요구되는 라이브러리 추가될때 마다 `tasks.json` 의 `args` 쪽에 위 구문을 추가한다
-   `cl.exe` 가 링커 작업을 할때 적절히 라이브러리를 포함 하는 작업을 해야 한다
