# VS Code C/C++ Debug With Cmake & vcpkg

VS Code 에서 Cmake & vcpkg 사용하여 디버깅 하는 템플릿

## 사용법

### 설치 (윈도우)

1. [mingw-w64 설치](https://github.com/niXman/mingw-builds-binaries/releases)

2. 설치된 `<mingw 경로>/bin`에 환경변수 설정하기


1. cmake 및 vcpkg 설치
    
    - `Visual Studio`애서 설치한경우 아래 경로를 환경변수 설정하면됨

        ```
        C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin

        C:\Program Files\Microsoft Visual Studio\2022\Community\VC\vcpkg
        ```


### 디버깅 가이드

VScode 에서 Cmake 탭에서 구성 부분 수정하면 MSVC, GCC 컴파일러 둘중 하나 선택할 수 있음

둘중 하나 선택해서 거기에 맞는 `launch.json` 구성 선택해서 디버깅 하면됨

### 라이브러리 추가

#### Vcpkg 에서 설치

```
vcpkg add port <라이브러리>
```

#### CMakeLists.txt 구성 추가

```text
find_package(<라이브러리> CONFIG REQUIRED)
target_link_libraries(<프로젝트 명> PRIVATE <라이브러리>::<해더파일 명>)
```