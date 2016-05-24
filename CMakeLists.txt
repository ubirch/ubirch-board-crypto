cmake_minimum_required(VERSION 3.0.2)
set(CMAKE_TOOLCHAIN_FILE ../ubirch-arm-toolchain/cmake/ubirch-arm-gcc-toolchain.cmake CACHE STRING "toolchain")
set(BOARD "ubirch1r02" CACHE STRING "board name")

project(ubirch-crypto C ASM)

require(PACKAGE ubirch BOARD ${BOARD} VERSION 1.0)
require(PACKAGE wolfssl MCU ${MCU} VERSION 3.9.0)

add_library(crypto ubirch/crypto/crypto.c)
target_link_libraries(crypto
        ubirch::${BOARD}::firmware
        wolfSSL::${MCU}::wolfcrypt)
target_include_directories(crypto PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

provide(PACKAGE ubirch-crypto VERSION 1.0 BOARD ${BOARD} TARGETS crypto)

find_package(Doxygen)
if (DOXYGEN_FOUND)
  configure_file(${CMAKE_CURRENT_SOURCE_DIR}/Doxyfile.in ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile @ONLY)
  add_custom_target(doc ALL
    ${DOXYGEN_EXECUTABLE} ${CMAKE_CURRENT_BINARY_DIR}/Doxyfile
    WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
    COMMENT "Generating API documentation with Doxygen" VERBATIM
    )
endif (DOXYGEN_FOUND)
