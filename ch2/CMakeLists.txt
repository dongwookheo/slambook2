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
# 공유 라이브러리
add_library(hello_shared SHARED libHelloSLAM.cpp)

# hello 라이브러리의 함수를 호출하는 실행 파일을 추가
add_executable(useHello useHello.cpp)
# 라이브러리 파일을 실행 파일에 연결
target_link_libraries(useHello hello_shared)
