cmake_minimum_required(VERSION 3.10)

set(MODULE_NAME x509)

find_package(OpenSSL REQUIRED)

# 添加链接库
set(EXTRA_LIBS ${EXTRA_LIBS} "${OPENSSL_LIBRARIES}")


# 添加头文件路径
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

# ======================================================
# 自动包含当前目录代码文件
# aux_source_directory(. DIR_SRCS)
set(x509_example_file "x509_example.cc")

# 生成可执行文件
add_executable(x509_example ${x509_example_file})

# 添加可执行文件使用的链接库
target_link_libraries(x509_example ${EXTRA_LIBS})

# 指定安装的文件信息
install(TARGETS x509_example DESTINATION bin)
#install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/Demo.h" DESTINATION include)


