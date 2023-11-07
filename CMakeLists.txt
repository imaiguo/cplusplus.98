
cmake_minimum_required(VERSION 3.5)

set(CMAKE_CXX_STANDARD 98)
set(AppName "cpp98test")
set(CMAKE_BUILD_TYPE Debug)
set(log4cplus_DIR D:/devtools/log4cplus-2.1.0/lib/cmake/log4cplus)

project (${AppName} LANGUAGES CXX)

find_package(log4cplus REQUIRED)
if(log4cplus_FOUND)
    message ("log4cplus found")
else()
    message (FATAL_ERROR "log4cplus isnot found")
endif()

link_directories(D:/devtools/googletest.1.12.0/debug/lib)

add_executable( ${AppName}
                src/main.cc
            )

INCLUDE_DIRECTORIES(${log4cplus_INCLUDE_DIRS} D:/devtools/googletest.1.12.0/debug/include)
TARGET_LINK_LIBRARIES(${AppName} PRIVATE log4cplus::log4cplusU gtest)

file( COPY config/log4cplus.properties DESTINATION ./)
