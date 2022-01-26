cmake_minimum_required(VERSION 3.15)

project( MulleObjCClionDemo C)

set( CMAKE_C_STANDARD 11)

#
# Install FoundationWrap into local folder "usr"
#
set( DEPENDENCY_DIR "usr")

include_directories( "generic")

include_directories( BEFORE SYSTEM "${DEPENDENCY_DIR}/include" )

find_library( C_WRAP_LIB NAMES ${CMAKE_STATIC_LIBRARY_PREFIX}c-wrap${CMAKE_STATIC_LIBRARY_SUFFIX}
              PATHS "${DEPENDENCY_DIR}/lib"
              NO_DEFAULT_PATH)

find_library( FOUNDATION_WRAP_LIB NAMES ${CMAKE_STATIC_LIBRARY_PREFIX}FoundationWrap${CMAKE_STATIC_LIBRARY_SUFFIX}
        PATHS "${DEPENDENCY_DIR}/lib"
        NO_DEFAULT_PATH)

find_library( FOUNDATION_WRAP_STARTUP_LIB NAMES ${CMAKE_STATIC_LIBRARY_PREFIX}FoundationWrap-startup${CMAKE_STATIC_LIBRARY_SUFFIX}
        PATHS "${DEPENDENCY_DIR}/lib"
        NO_DEFAULT_PATH)


if( UNIX)
link_libraries( -Wl,--whole-archive ${FOUNDATION_WRAP_LIB} -Wl,--no-whole-archive)
link_libraries( -Wl,--export-dynamic -Wl,--whole-archive ${FOUNDATION_WRAP_STARTUP_LIB} -Wl,--no-whole-archive)
else()
message( FATAL_ERROR "unsupported platform")
endif()

link_libraries( ${C_WRAP_LIB})

if( UNIX)
link_libraries( -ldl)
link_libraries( -lm)
endif()

#
# managed by CLion
#
add_executable( ${PROJECT_NAME} main.m FooBar.m FooBar.h generic/import-private.h generic/import.h)
