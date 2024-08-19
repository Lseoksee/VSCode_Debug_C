# VS Code C/C++ Debug With MSCV

VS Code 에서 GCC 가 아닌 Visual Studio의 컴파일러 MSCV(cl.exe)를 사용하여 디버깅 하는 템플릿

## 사용법

1. `Visual Studio 2022` 설치하기

2. `cl.exe` 경로 환경 변수 설정하기

    - 보통은 이경로

        ```text
        C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC\14.40.33807\bin\Hostx64\x64
        ```

3. 자기 경로에 맞게 `tasks.json` 경로 수정하기

    - `tasks.json`안에 수정 고려사항 목록

        ```text
        "C:/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.40.33807/include"
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.22621.0/ucrt"
        "/LIBPATH:C:/Program Files/Microsoft Visual Studio/2022/Community/VC/Tools/MSVC/14.40.33807/lib/onecore/x64"
        "/LIBPATH:C:/Program Files (x86)/Windows Kits/10/Lib/10.0.22621.0/um/x64",
        "/LIBPATH:C:/Program Files (x86)/Windows Kits/10/Lib/10.0.22621.0/ucrt/x64"
        ```

4. VS Code에서 코드를 작성하고 디버깅 시작하기
    > `exe` 파일 생성은 `bin/` 폴더에 생성되니 바꾸고 싶으면 `tasks.json` 수정
