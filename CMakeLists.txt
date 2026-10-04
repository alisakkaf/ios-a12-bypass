cmake_minimum_required(VERSION 3.20)

project(a12_bypass
    VERSION 2.1.0
    DESCRIPTION "Professional iOS Activation Solution for A12+ Devices"
    LANGUAGES CXX
)

# ============================================================================
# Project Configuration
# ============================================================================

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# Build type defaults to Release
if(NOT CMAKE_BUILD_TYPE AND NOT CMAKE_CONFIGURATION_TYPES)
    message(STATUS "Setting build type to 'Release' as none was specified")
    set(CMAKE_BUILD_TYPE Release CACHE STRING "Choose the type of build" FORCE)
    set_property(CACHE CMAKE_BUILD_TYPE PROPERTY STRINGS "Debug" "Release" "MinSizeRel" "RelWithDebInfo")
endif()

# ============================================================================
# Compiler Configuration
# ============================================================================

add_library(project_warnings INTERFACE)
add_library(project_options INTERFACE)

target_compile_features(project_options INTERFACE cxx_std_20)

# Compiler-specific warnings
if(CMAKE_CXX_COMPILER_ID MATCHES "GNU|Clang|AppleClang")
    target_compile_options(project_warnings INTERFACE
        -Wall
        -Wextra
        -Wpedantic
        -Wshadow
        -Wnon-virtual-dtor
        -Wold-style-cast
        -Wcast-align
        -Wunused
        -Woverloaded-virtual
        -Wconversion
        -Wsign-conversion
        -Wnull-dereference
        -Wdouble-promotion
        -Wformat=2
        -Wimplicit-fallthrough
    )
    
    if(CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        target_compile_options(project_warnings INTERFACE
            -Wmisleading-indentation
            -Wduplicated-cond
            -Wduplicated-branches
            -Wlogical-op
            -Wuseless-cast
        )
    endif()
endif()

# Debug/Release specific options
target_compile_options(project_options INTERFACE
    $<$<CONFIG:Debug>:-O0 -g3 -fno-omit-frame-pointer>
    $<$<CONFIG:Release>:-O3 -DNDEBUG>
    $<$<CONFIG:RelWithDebInfo>:-O2 -g>
)

# ============================================================================
# Platform Configuration
# ============================================================================

if(APPLE)
    set(CMAKE_MACOSX_RPATH ON)
    
    # Homebrew paths for both Intel and Apple Silicon
    list(APPEND CMAKE_PREFIX_PATH 
        "/opt/homebrew"
        "/opt/homebrew/opt/sqlite"
        "/usr/local"
        "/usr/local/opt/sqlite"
    )
    
    # pkg-config paths
    set(ENV{PKG_CONFIG_PATH} 
        "/opt/homebrew/lib/pkgconfig:/opt/homebrew/opt/sqlite/lib/pkgconfig:/usr/local/lib/pkgconfig:/usr/local/opt/sqlite/lib/pkgconfig:$ENV{PKG_CONFIG_PATH}"
    )
endif()

# ============================================================================
# Dependencies
# ============================================================================

find_package(PkgConfig REQUIRED)

# libimobiledevice suite
pkg_check_modules(IMOBILEDEVICE REQUIRED IMPORTED_TARGET libimobiledevice-1.0)
pkg_check_modules(PLIST REQUIRED IMPORTED_TARGET libplist-2.0)
pkg_check_modules(USBMUXD REQUIRED IMPORTED_TARGET libusbmuxd-2.0)
pkg_check_modules(IDEVICE_GLUE REQUIRED IMPORTED_TARGET libimobiledevice-glue-1.0)

# SQLite3
find_package(SQLite3 REQUIRED)

# libzip
pkg_check_modules(LIBZIP REQUIRED IMPORTED_TARGET libzip)

# Threads
find_package(Threads REQUIRED)

# ============================================================================
# Source Files
# ============================================================================

set(BYPASS_SOURCES
    src/main.cpp
    src/core/logger.cpp
    src/core/error.cpp
    src/device/device_manager.cpp
    src/device/afc_client.cpp
    src/device/diagnostics_client.cpp
    src/device/syslog_client.cpp
    src/payload/sqlite_builder.cpp
    src/payload/epub_builder.cpp
    src/payload/payload_generator.cpp
    src/utils/guid_extractor.cpp
    src/utils/plist_utils.cpp
    src/bypass/bypass_controller.cpp
)

set(BYPASS_HEADERS
    include/iCloudBypassA12/core/types.hpp
    include/iCloudBypassA12/core/result.hpp
    include/iCloudBypassA12/core/error.hpp
    include/iCloudBypassA12/core/logger.hpp
    include/iCloudBypassA12/core/raii.hpp
    include/iCloudBypassA12/device/device_manager.hpp
    include/iCloudBypassA12/device/afc_client.hpp
    include/iCloudBypassA12/device/diagnostics_client.hpp
    include/iCloudBypassA12/device/syslog_client.hpp
    include/iCloudBypassA12/payload/sqlite_builder.hpp
    include/iCloudBypassA12/payload/epub_builder.hpp
    include/iCloudBypassA12/payload/payload_generator.hpp
    include/iCloudBypassA12/utils/guid_extractor.hpp
    include/iCloudBypassA12/utils/plist_utils.hpp
    include/iCloudBypassA12/bypass/bypass_controller.hpp
    include/iCloudBypassA12/bypass/config.hpp
)

# ============================================================================
# Target Definition
# ============================================================================

add_executable(${PROJECT_NAME} ${BYPASS_SOURCES} ${BYPASS_HEADERS})

target_include_directories(${PROJECT_NAME} 
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_link_libraries(${PROJECT_NAME}
    PRIVATE
        project_warnings
        project_options
        PkgConfig::IMOBILEDEVICE
        PkgConfig::PLIST
        PkgConfig::USBMUXD
        PkgConfig::IDEVICE_GLUE
        PkgConfig::LIBZIP
        SQLite3::SQLite3
        Threads::Threads
)

target_compile_definitions(${PROJECT_NAME}
    PRIVATE
        BYPASS_VERSION="${PROJECT_VERSION}"
        BYPASS_RESOURCES_DIR="${CMAKE_CURRENT_SOURCE_DIR}/resources"
        $<$<BOOL:${APPLE}>:BYPASS_PLATFORM_MACOS>
)

# ============================================================================
# Post-Build
# ============================================================================

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory
        ${CMAKE_CURRENT_SOURCE_DIR}/resources
        $<TARGET_FILE_DIR:${PROJECT_NAME}>/resources
    COMMENT "Copying resources to build directory"
)

# ============================================================================
# Installation
# ============================================================================

include(GNUInstallDirs)

install(TARGETS ${PROJECT_NAME}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

install(DIRECTORY resources/
    DESTINATION ${CMAKE_INSTALL_DATADIR}/${PROJECT_NAME}/resources
)

# ============================================================================
# Summary
# ============================================================================

message(STATUS "")
message(STATUS "━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━")
message(STATUS "  ${PROJECT_NAME} v${PROJECT_VERSION}")
message(STATUS "  Professional iOS Activation Solution for A12+ Devices")
message(STATUS "━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━")
message(STATUS "Build type:           ${CMAKE_BUILD_TYPE}")
message(STATUS "C++ Standard:         ${CMAKE_CXX_STANDARD}")
message(STATUS "Compiler:             ${CMAKE_CXX_COMPILER_ID} ${CMAKE_CXX_COMPILER_VERSION}")
message(STATUS "")
message(STATUS "Dependencies:")
message(STATUS "  libimobiledevice:   ${IMOBILEDEVICE_VERSION}")
message(STATUS "  libplist:           ${PLIST_VERSION}")
message(STATUS "  libzip:             ${LIBZIP_VERSION}")
message(STATUS "  SQLite3:            ${SQLite3_VERSION}")
message(STATUS "━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━")
message(STATUS "")

# ============================================================================
# Testing
# ============================================================================

option(BUILD_TESTS "Build unit tests" ON)

if(BUILD_TESTS)
    include(FetchContent)
    
    FetchContent_Declare(
        Catch2
        GIT_REPOSITORY https://github.com/catchorg/Catch2.git
        GIT_TAG        v3.5.2
    )
    
    FetchContent_MakeAvailable(Catch2)
    
    # Test sources
    set(TEST_SOURCES
        tests/test_main.cpp
        tests/test_core.cpp
        tests/test_utils.cpp
        tests/test_payload.cpp
    )
    
    # Library target for testing (excludes main.cpp)
    set(LIB_SOURCES
        src/core/logger.cpp
        src/core/error.cpp
        src/device/device_manager.cpp
        src/device/afc_client.cpp
        src/device/diagnostics_client.cpp
        src/device/syslog_client.cpp
        src/payload/sqlite_builder.cpp
        src/payload/epub_builder.cpp
        src/payload/payload_generator.cpp
        src/utils/guid_extractor.cpp
        src/utils/plist_utils.cpp
        src/bypass/bypass_controller.cpp
    )
    
    add_library(a12bypass_lib STATIC ${LIB_SOURCES})
    
    target_include_directories(a12bypass_lib
        PUBLIC
            ${CMAKE_CURRENT_SOURCE_DIR}/include
    )
    
    target_link_libraries(a12bypass_lib
        PUBLIC
            project_options
            PkgConfig::IMOBILEDEVICE
            PkgConfig::PLIST
            PkgConfig::USBMUXD
            PkgConfig::IDEVICE_GLUE
            PkgConfig::LIBZIP
            SQLite3::SQLite3
            Threads::Threads
    )
    
    target_compile_definitions(a12bypass_lib
        PUBLIC
            BYPASS_VERSION="${PROJECT_VERSION}"
            BYPASS_RESOURCES_DIR="${CMAKE_CURRENT_SOURCE_DIR}/resources"
            $<$<BOOL:${APPLE}>:BYPASS_PLATFORM_MACOS>
    )
    
    # Test executable
    add_executable(a12bypass_tests ${TEST_SOURCES})
    
    target_link_libraries(a12bypass_tests
        PRIVATE
            a12bypass_lib
            Catch2::Catch2WithMain
    )
    
    target_include_directories(a12bypass_tests
        PRIVATE
            ${CMAKE_CURRENT_SOURCE_DIR}/include
    )
    
    # Disable warnings for test code
    target_compile_options(a12bypass_tests PRIVATE -w)
    
    # CTest integration
    include(CTest)
    include(Catch)
    catch_discover_tests(a12bypass_tests)
    
    message(STATUS "Tests:                Enabled")
else()
    message(STATUS "Tests:                Disabled")
endif()
