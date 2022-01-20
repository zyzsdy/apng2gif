cmake_minimum_required(VERSION 3.10)
project (apng2gif)

find_library(MATH_LIBRARY m)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# zlib
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/libs/zlib ZLIB_SOURCES)
add_library (zlib ${ZLIB_SOURCES})

# libpng
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/libs/libpng LIBPNG_SOURCES)
add_library (libpng ${LIBPNG_SOURCES})
target_include_directories(libpng PRIVATE ${CMAKE_CURRENT_LIST_DIR}/libs/zlib)
if(MATH_LIBRARY)
    target_link_libraries(libpng PRIVATE ${MATH_LIBRARY})
endif()
target_link_libraries(libpng PRIVATE zlib)

#apng2gif
aux_source_directory(${CMAKE_CURRENT_LIST_DIR}/src APNG2GIF_SOURCES)
add_executable(apng2gif ${APNG2GIF_SOURCES})
target_include_directories(apng2gif PRIVATE ${CMAKE_CURRENT_LIST_DIR}/libs/zlib ${CMAKE_CURRENT_LIST_DIR}/libs/libpng)
target_link_libraries(apng2gif PRIVATE zlib libpng)

install (TARGETS apng2gif DESTINATION "${CMAKE_CURRENT_LIST_DIR}/bin")