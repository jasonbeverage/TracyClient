CMAKE_MINIMUM_REQUIRED(VERSION 3.1 FATAL_ERROR)

SET(CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/CMakeModules)

project(TracyClient)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_library(TracyClient SHARED
            tracy/TracyClient.cpp
            )
target_include_directories(TracyClient PUBLIC tracy)
target_compile_definitions(TracyClient PRIVATE TRACY_ENABLE TRACY_ONDEMAND TRACY_EXPORTS)

install(TARGETS TracyClient
        RUNTIME DESTINATION bin
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
)

install(DIRECTORY tracy/ DESTINATION include)
