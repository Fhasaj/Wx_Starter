## Base for my wxWidgets Applications
## Use When creating a wxWidgets application to get
## the application to build using Cmake on all platforms

## Copyright (c) 2025 Fatlum Hasaj. All Rights Reserved.

cmake_minimum_required(VERSION 3.16)
project(MyWxApp) # CHnage Application Name here

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add wxWidgets subdirectory (assumes CMake-based build)
add_subdirectory(lib/wxWidgets)

# wxWidgets setup - define components you need
set(wxWidgets_COMPONENTS core base)
find_package(wxWidgets REQUIRED COMPONENTS ${wxWidgets_COMPONENTS})

# Include wxWidgets use file
include(${wxWidgets_USE_FILE})

# Include directories
include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/headers
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/wxWidgets/include
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/wxWidgets/lib
)

# Source files
file(GLOB_RECURSE SRC_FILES src/*.cpp)
file(GLOB_RECURSE HDR_FILES headers/*.h)

# Create executable
add_executable(${PROJECT_NAME} ${SRC_FILES} ${HDR_FILES})

# Link wxWidgets
target_link_libraries(${PROJECT_NAME} ${wxWidgets_LIBRARIES})

