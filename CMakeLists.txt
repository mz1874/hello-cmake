# cmake 需要的版本
cmake_minimum_required(VERSION 3.25)

# 项目名称
project(LearnCmake)

# 设置 C++ 环境宏, 使用不同的 C++ 特性进行编译
set(CMAKE_CXX_STANDARD 17)


# 建议使用绝对路径
set(HOME ${CMAKE_BINARY_DIR})

# 设置编译程序的输出目录
set(EXECUTABLE_OUTPUT_PATH ${HOME}/bin)


#查找头文件
include_directories(${PROJECT_SOURCE_DIR}/include)

#用来查找源文件的
#aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR}/source SRC)

#或者使用file
#file(GLOB FILE ${CMAKE_CURRENT_SOURCE_DIR}/source/*.cpp)

# 动态库文件也可以指定输出的位置, 如果目录不存在的话, CMAKE 会帮我们自动创建
set(LIBRARY_OUTPUT_PATH ${HOME}/lib)
#也可以使用 配置库文件的目录
#set(EXECUTABLE_OUTPUT_PATH ${HOME}/lib)
# 编译的执行文件

#制作动态链接库, 静态库 STATIC 动态库SHARED
add_library(hello STATIC ${PROJECT_SOURCE_DIR}/include/Hello.h ${PROJECT_SOURCE_DIR}/source/Hello.cpp)

#链接静态库
link_libraries(hello)
#链接静态库目录
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/lib)

add_executable(app ${FILE} ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp)
