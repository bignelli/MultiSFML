cmake_minimum_required(VERSION 3.14)
set(PROJECT_NAME "MultiSFML")
project(${PROJECT_NAME})
#set(SFML_DIR "${CMAKE_CURRENT_LIST_DIR}/libs/SFML-2.5.1/lib/cmake/SFML") #needed if dir is non standard

#Because Windows
IF (WIN32)
file(GLOB ALL_REQUIRED_DLL "libs/required_dlls/*.dll")
file(COPY ${ALL_REQUIRED_DLL} DESTINATION ${CMAKE_CURRENT_BINARY_DIR})
ENDIF()
#End copying of Dlls

set(CMAKE_CXX_STANDARD 14)

link_libraries(stdc++fs) #link the filesystem

file(GLOB_RECURSE SCRF "src/*.cpp" "src/*.hpp")
#include_directories("src/Util")
add_executable(${PROJECT_NAME} ${SCRF} main.cpp )
find_package(SFML 2.5.1 COMPONENTS system window graphics network audio REQUIRED)
target_link_libraries(${PROJECT_NAME} sfml-audio sfml-graphics sfml-window sfml-system)