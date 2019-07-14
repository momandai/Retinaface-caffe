cmake_minimum_required(VERSION 3.5)
project(retina-caffe)

set(CMAKE_CXX_STANDARD 14)

add_definitions(-D CPU_ONLY)



file(GLOB_RECURSE SRC
        src/*.h
        src/*.cpp
        )
foreach(f ${SRC})
    message(${f})
endforeach(f)
set(SOURCE_FILES SRC)

set(SOURCE_DIR src)

include_directories(/usr/include/caffe)

find_package(OpenCV REQUIRED)

find_package(Boost REQUIRED)

add_executable(${PROJECT_NAME} ${SRC})

target_link_libraries(${PROJECT_NAME} boost_system caffe glog protobuf gflags ${OpenCV_LIBS})