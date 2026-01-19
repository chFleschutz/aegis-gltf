cmake_minimum_required(VERSION 3.28)

project(aegis-gltf LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_TEST "Build test project" ON)

# Enable test project if this is the root project
if(CMAKE_SOURCE_DIR STREQUAL PROJECT_SOURCE_DIR)
    set(BUILD_TEST ON)
endif()


add_library(${PROJECT_NAME} STATIC)
add_library(Aegis::GLTF ALIAS ${PROJECT_NAME})

target_sources(${PROJECT_NAME} PRIVATE
    "gltf.cpp"
)

target_include_directories(${PROJECT_NAME} PUBLIC
	"${CMAKE_CURRENT_SOURCE_DIR}"
	"${CMAKE_CURRENT_SOURCE_DIR}/lib"
)


if(BUILD_TEST)
	add_subdirectory("test")
endif()
