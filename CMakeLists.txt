cmake_minimum_required(VERSION 3.10)
project(rest_server)

set(CMAKE_CXX_STANDARD 17)

find_package(PostgreSQL REQUIRED)

find_library(PQXX_LIB pqxx REQUIRED)

add_executable(rest_server main.cpp)

target_include_directories(rest_server PRIVATE 
    ${PostgreSQL_INCLUDE_DIRS}
    /usr/local/include
)

target_link_libraries(rest_server PRIVATE 
    ${PQXX_LIB}
    ${PostgreSQL_LIBRARIES}
    pthread
)
