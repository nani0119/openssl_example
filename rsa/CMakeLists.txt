cmake_minimum_required(VERSION 3.10)

set(MODULE_NAME rsa)

find_package(OpenSSL REQUIRED)

# 添加链接库
set(EXTRA_LIBS ${EXTRA_LIBS} "${OPENSSL_LIBRARIES}")


# 添加头文件路径
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

# ======================================================
# 自动包含当前目录代码文件
# aux_source_directory(. DIR_SRCS)
set(rsa_example_file "rsa_example.cc")

# 生成可执行文件
add_executable(rsa_example ${rsa_example_file})

# 添加可执行文件使用的链接库
target_link_libraries(rsa_example ${EXTRA_LIBS})

# 指定安装的文件信息
install(TARGETS rsa_example DESTINATION bin)
#install(FILES "${CMAKE_CURRENT_SOURCE_DIR}/test.cnf" DESTINATION bin)