CMAKE_MINIMUM_REQUIRED ( VERSION 2.6)

PROJECT( pmplayground )

## set output directory
SET ( CMAKE_RUNTIME_OUTPUT_DIRECTORY ${pmplayground_SOURCE_DIR}/../bin )
SET (pmplayground_BINARY_DIR ${CMAKE_RUNTIME_OUTPUT_DIRECTORY})

FILE ( GLOB clflush_test_SRC "${pmplayground_SOURCE_DIR}/../src/clflush_test.c" )

ADD_EXECUTABLE ( clflush_test  ${clflush_test_SRC} )

# set the path for libraries
INCLUDE_DIRECTORIES (
    ${pmplayground_SOURCE_DIR}/../src/include
    ${pmplayground_SOURCE_DIR}/../lib/include
)

LINK_DIRECTORIES(
    ${pmplayground_SOURCE_DIR}/../lib/lib
)

TARGET_LINK_LIBRARIES ( clflush_test
    ${pmplayground_SOURCE_DIR}/../lib/lib/libpmem.a
)


SET ( GCC_COMPILE_FLAGS "-Wall -std=c++0x -O3")
SET ( GCC_LINK_FLAGS    "-static-libgcc -Wall -O3")

SET( CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} ${GCC_COMPILE_FLAGS}" )
SET( CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${GCC_LINK_FLAGS}" )