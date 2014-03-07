cmake_minimum_required( VERSION 2.8 )
project( libpizip )

set( CMAKE_BUILD_TYPE Release CACHE STRING "Build type." FORCE )
set( LIBPIZIP_BUILD_SHARED_LIBS TRUE CACHE BOOL "Build shared llibraries." )
set( LIBPIZIP_BUILD_DOCS TRUE CACHE BOOL "Build Doxygen documentation." )
#set( LIBPIZIP_BUILD_EXAMPLES TRUE CACHE BOOL "Build LIBPIZIP examples." )

if(CMAKE_COMPILER_IS_GNUCXX)
        set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
endif()

if( LIBPIZIP_BUILD_SHARED_LIBS )
        set( LIB_TYPE SHARED )
else()
        set( LIB_TYPE STATIC )
endif()

set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake/Modules/;${CMAKE_MODULE_PATH}")

set(SRC_DIR "src")
set(INC_DIR "include")

set(
	SOURCES
	${CMAKE_PROJECT_NAME}/${INC_DIR}/${CMAKE_PROJECT_NAME}/libpizip.hpp
	${CMAKE_PROJECT_NAME}/${SRC_DIR}/${CMAKE_PROJECT_NAME}/libpizip.cpp
)

include_directories( ${CMAKE_PROJECT_NAME}/${INC_DIR} )

add_library( ${CMAKE_PROJECT_NAME} ${LIB_TYPE} ${SOURCES} )

# if( LIBPIZIP_BUILD_DOCS )
# 	configure_file(${CMAKE_BINARY_DIR}/docs/Doxyfile.in ${CMAKE_BINARY_DIR}/docs/Doxyfile @ONLY)
#     set(DOXYGEN_SKIP_DOT TRUE)
#     find_package(Doxygen)
# 	add_subdirectory( docs )
# endif()


# if( LIBPIZIP_BUILD_EXAMPLES )
# 	include(examples/CMakeLists.txt)
# endif()
