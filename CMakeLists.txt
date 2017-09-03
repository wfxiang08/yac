cmake_minimum_required(VERSION 3.2)
project(yac)


set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

# 使用php7.1，保持和线上代码一致
INCLUDE_DIRECTORIES(
    /usr/local/Cellar/php71/7.1.5_17/include/php
    /usr/local/Cellar/php71/7.1.5_17/include/php/main
    /usr/local/Cellar/php71/7.1.5_17/include/php/Zend
    ./
)

set(SOURCE_FILES
    compressor/fastlz/fastlz.c
    compressor/fastlz/fastlz.h
    serializer/msgpack.c
    serializer/php.c
    serializer/yac_serializer.h
    storage/allocator/allocators/createfilemapping.c
    storage/allocator/allocators/mmap.c
    storage/allocator/allocators/shm.c
    storage/allocator/yac_allocator.c
    storage/allocator/yac_allocator.h
    storage/yac_storage.c
    storage/yac_storage.h
    php_yac.h
    yac.c)

add_executable(yac ${SOURCE_FILES})