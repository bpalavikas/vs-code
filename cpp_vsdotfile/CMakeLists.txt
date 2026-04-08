# Single target
cmake_minimum_required(VERSION 3.16)

project(<PROJECT_NAME> VERSION 1.0 LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(<TARGET_NAME>
    src/main.cpp
)

target_include_directories(<TARGET_NAME>
    PRIVATE
        include
)

# multi target
cmake_minimum_required(VERSION 3.16)

project(<PROJECT_NAME> VERSION 1.0 LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# ---- Targets ----

add_executable(<TARGET1>
    src/<file1>.cpp
)

add_executable(<TARGET2>
    src/<file2>.cpp
)

# ---- Common includes ----

target_include_directories(<TARGET1> PRIVATE include)
target_include_directories(<TARGET2> PRIVATE include)


# multi target with shared common libraries
cmake_minimum_required(VERSION 3.16)

project(<PROJECT_NAME> VERSION 1.0 LANGUAGES CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# ---- Common warnings ----

add_compile_options(
    -Wall
    -Wextra
    -Wpedantic
)

# ---- Shared library ----

add_library(common_lib
    src/common/config.cpp
    src/common/protocol.cpp
)

target_include_directories(common_lib
    PUBLIC
        ${CMAKE_SOURCE_DIR}/include
)

# ---- Frontend executable ----

add_executable(frontend_app
    src/frontend/main.cpp
    src/frontend/ui.cpp
)

target_link_libraries(frontend_app
    PRIVATE
        common_lib
)

# ---- Backend executable ----

add_executable(backend_app
    src/backend/main.cpp
    src/backend/server.cpp
)

target_link_libraries(backend_app
    PRIVATE
        common_lib
)
