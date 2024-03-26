# cmake 최소 버전 명시
cmake_minimum_required(VERSION 2.8)

# cmake 프로젝트 선언
project(HelloSLAM)

# 컴파일 모드 설정
set(CMAKE_BUILD_TYPE "Debug")

# 실행 파일 추가
# 문법: add_executable(<프로그램 이름> <소스 파일 이름>)
add_executable(helloSLAM helloSLAM.cpp)

# hello 라이브러리 추가
add_library(hello libHelloSLAM.cpp)
# 공유 라이브러리: Static library와 다르게 실행 시, load되는 library. 연결된 외부 library를 실행 프로그램에
# 포함시키지 않기 때문에 용량에 이점이 있음. 또한, 외부 library가 업그레이드 될 경우 재컴파일 되는 귀찮음도 덜어짐.
# 하지만, 배포의 단순성과 모든 시스템에 라이브러리가 존재하고 올바르게 버전이 관리되어야 한다는 단점으로 static library를 선호하기도 함.
add_library(hello_shared SHARED libHelloSLAM.cpp)

# hello 라이브러리의 함수를 호출하는 실행 파일을 추가
add_executable(useHello useHello.cpp)
# 라이브러리 파일을 실행 파일에 연결
target_link_libraries(useHello hello_shared)
