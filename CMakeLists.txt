cmake_minimum_required(VERSION 2.8.7)

set(CMAKE_DISABLE_SOURCE_CHANGES ON)
set(CMAKE_DISABLE_IN_SOURCE_BUILD ON)

find_program(NASM_BIN nasm)

if (${NASM_BIN} STREQUAL NASM_BIN-NOTFOUND)
  message(FATAL_ERROR "NASM not found. Can not build project.")
endif()

enable_language(ASM_NASM)

project(vboot ASM_NASM)

set(CMAKE_ASM_NASM_COMPILE_OBJECT "${NASM_BIN} <SOURCE> -f bin -o <OBJECT>")
set(CMAKE_ASM_NASM_LINK_EXECUTABLE "cp <OBJECTS> <TARGET>")

add_executable(vboot.img boot.asm)
