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
    wx::base      # Core non-GUI classes (like strings, arrays, file handling, threads, etc.).
    wx::core      # Core GUI classes (like windows, dialogs, events, device contexts). Most basic GUI apps need this.
    wx::adv       # Advanced GUI controls and features (like wizards, calendars, animation controls).
    wx::aui       # Advanced User Interface — supports docking/floating panes, customizable layouts (like those in IDEs)
    wx::html      # HTML rendering and simple browser-like controls. Good for rich-text display and help systems.
    wx::xrc       # XML Resource system — allows you to define GUI layouts using XML files, rather than hard-coding them.
    wx::net       # Networking functionality, such as sockets and URL handling.
    wx::xml       # XML parser module. Useful for reading and writing custom XML files.
    wx::richtext  # Rich Text control — supports styled text, images, and formatting (like a basic word processor).
    wx::media     # Media playback module — allows playing audio and video files within applications.
    wx::webview   # Embeds a native web browser control (using platform-native engines like WebKit or Edge).
    wx::gl        # OpenGL support — allows integration of OpenGL rendering in wxWidgets windows.
    wx::stc       # Styled Text Control — based on Scintilla, used for syntax-highlighted editors.
    wx::propgrid  # Property Grid control — ideal for object/property editors (common in IDEs or editors).
    wx::ribbon    # Ribbon-style interface controls (like Microsoft Office ribbons).
    wx::qa        # Quality Assurance — mainly for testing and diagnostics of wxWidgets internals.
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

