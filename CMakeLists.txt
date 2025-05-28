# -----------------------------------------------------------------------------
# Base for my wxWidgets Applications
# Use When creating a wxWidgets application to get
# the application to build using CMake on all platforms
# -----------------------------------------------------------------------------

# Copyright (c) 2025 Fatlum Hasaj. All Rights Reserved.

cmake_minimum_required(VERSION 3.16)
project(MyWxApp)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# -----------------------------------------------------------------------------
# Add wxWidgets (built as a subproject)
# -----------------------------------------------------------------------------
set(wxBUILD_SHARED OFF CACHE BOOL "Build wxWidgets as a static library")
set(wxUSE_UNICODE ON CACHE BOOL "Enable Unicode support")
set(BUILD_SHARED_LIBS OFF CACHE BOOL "Disable shared libs for wxWidgets")
set(wxBUILD_MONOLITHIC OFF CACHE BOOL "Use monolithic build OFF")
set(wxBUILD_SAMPLES OFF CACHE BOOL "Don't build wxWidgets samples")
set(wxBUILD_DEMOS OFF CACHE BOOL "Don't build wxWidgets demos")
set(wxBUILD_TESTS OFF CACHE BOOL "Don't build wxWidgets tests")

# Add wxWidgets subdirectory
add_subdirectory(lib/wxWidgets)

# -----------------------------------------------------------------------------
# Include directories for your app
# -----------------------------------------------------------------------------
include_directories(
    ${CMAKE_CURRENT_SOURCE_DIR}/headers
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/wxWidgets/include
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/wxWidgets/lib
)

# -----------------------------------------------------------------------------
# Collect source files
# -----------------------------------------------------------------------------
file(GLOB_RECURSE SRC_FILES src/*.cpp)
file(GLOB_RECURSE HDR_FILES headers/*.h)

# -----------------------------------------------------------------------------
# Create the executable
# -----------------------------------------------------------------------------
add_executable(${PROJECT_NAME} ${SRC_FILES} ${HDR_FILES})

# -----------------------------------------------------------------------------
# Link against wxWidgets libraries
# -----------------------------------------------------------------------------
# Find all relevant built libraries
set(WX_LIBS
    wx::base
    wx::core
    wx::adv
    wx::aui
    wx::html
    wx::xrc
    wx::net
    wx::xml
    wx::richtext
    wx::media
    wx::webview
    wx::gl
    wx::stc
    wx::propgrid
    wx::ribbon
    wx::qa
)

target_link_libraries(${PROJECT_NAME} PRIVATE ${WX_LIBS})

# -----------------------------------------------------------------------------
# Platform-specific tweaks (if needed)
# -----------------------------------------------------------------------------
if(WIN32)
    set_target_properties(${PROJECT_NAME} PROPERTIES
        WIN32_EXECUTABLE TRUE
    )    
target_compile_definitions(${PROJECT_NAME} PRIVATE _CRT_SECURE_NO_WARNINGS)
endif()

