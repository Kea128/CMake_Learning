cmake_minimum_required(VERSION 3.0.0)
project(test_0730)

# 设置c++版本
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# 查找gflags库
find_package(gflags REQUIRED)

# 查找glog库
find_package(glog REQUIRED)

# 包含头文件路径
# ${CMAKE_CURRENT_SOURCE_DIR}表示CMakeLists所在的路径，和${PROJECT_SOURCE_DIR}一致
include_directories(${PROJECT_SOURCE_DIR}/include)

# 查找所有源文件
file(GLOB_RECURSE SRC_LIST ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cc)

# 除去main.cc
list(REMOVE_ITEM SRC_LIST ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cc)

# 添加可执行文件
add_executable(main src/main.cc)

# 链接gflags库和glog库
target_link_libraries(main gflags glog::glog)

# 可执行文件存放位置
# set(EXECUTABLE_OUTPUT_PATH ../bin) #这个也可以，因为make时在build目录下，需要..
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/bin)
