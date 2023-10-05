# 版本号
cmake_minimum_required(VERSION 3.27.5)

# 项目名
project(test)

# mingw32-make
# 如果下的c包里不是该名称则改掉

# cmake -G "MinGW Cmakefiles"
# 如果cmake默认选项不是MinGW，可以添加-G选项，或通过GUI清理缓存后再试试



# 一些宏
# CmakeLists文件的当前位置
set(HOME ${CMAKE_CURRENT_SOURCE_DIR})
# 输出某个变量
MESSAGE("#######${CMAKE_CURRENT_SOURCE_DIR}#######")
# 指定可执行程序输出的路径
set(EXECUTABLE_OUTPUT_PATH ${HOME}/build)
# 静态库生成的位置
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${HOME}/lib)
MESSAGE("#######${CMAKE_ARCHIVE_OUTPUT_DIRECTORY}#######")
# 动态库生成的位置
# set(EXECUTABLE_OUTPUT_PATH "xxx")

# 包含静态/动态库所在路径
include_directories(${CMAKE_ARCHIVE_OUTPUT_DIRECTORY})

# 添加静态库
# 将静态库名libXXX.a与文件链接起来
add_library(function
    STATIC
    function.cpp
)
# 链接静态库
link_libraries(
    function
)

# 链接动态库
# 动态库名libXXX.so
# target_link_libraries(
#     app
#     lib_name
# )

# 将文件添加至可执行二进制
add_executable(app test.cpp)
