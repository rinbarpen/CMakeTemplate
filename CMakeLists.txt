cmake_minimum_required (VERSION 3.4)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

project ("Template" VERSION 0.1 LANGUAGES C CXX)

if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Debug")
endif()
message("Build ${PROJECT_NAME} with ${CMAKE_BUILD_TYPE}")

set(EXECUTABLE_OUTPUT_PATH "${CMAKE_SOURCE_DIR}/bin/${CMAKE_BUILD_TYPE}")

######################################### Requirments Download ########################################
add_subdirectory("3rdparty")
######################################### Requirments Download ########################################

######################################### Library Begin ############################################
set(LIB_DIR "lib")
#add_subdirectory("${LIB_DIR}/zlib")

######################################### Library End   ############################################

#find_package(OpenSSL COMPONENTS SSL Crypto REQUIRED)
#find_program(ClangFormat REQUIRED)

#find_package(Qt5 REQUIRED COMPONENTS Widgets Gui Core Sql REQUIRED)

file(GLOB_RECURSE
    CoreSrcs
        CONFIGURE_DEPENDS
        "src/${PROJECT_NAME}/*.cpp"
)

message(STATUS "SRC FILES: ${CoreSrcs}")

add_executable (${PROJECT_NAME} "src/main.cpp" ${CoreSrcs})

target_include_directories(${PROJECT_NAME}
    PRIVATE
        "${CMAKE_SOURCE_DIR}/include"
        "${LIB_DIR}"
)

target_link_libraries(${PROJECT_NAME}
    PUBLIC
        fmt::fmt
        yaml-cpp::yaml-cpp
#        zlibstatic
#        OpenSSL::SSL
#        OpenSSL::Crypto
#        range-v3
#        tl::expected
)

target_compile_features(${PROJECT_NAME}
    PUBLIC
        cxx_std_17
)
