# Minimal CMakeLists.txt for a simple C project
# This ensures that if someone has an outdated CMake version,
# they will get a clear error instead of unexpected behavior.
# Version 3.16 is a safe choice.
cmake_minimum_required(VERSION 3.16)

# Name of the project "MinimalC" and specify the language C.
project(MinimalC C)

# Set the C language standard
# The first line: require at least C99.
# The second line: make this requirement mandatory.
set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)

# Create executable "main" from source files
# The add_executable() function tells CMake: 
# "I want to build a program named main"
# (on Windows this will produce main.exe).
# After the program name, we list all source files.
# In this case: main.c and hello/hello.c
add_executable(main
    main.c        # main module
    hello/hello.c # additional module
)

# Add header directories
# target_include_directories() is the equivalent of the compiler flag -I.
# Here, we add the "hello" directory where hello.h is located.
# Thanks to this, in main.c we can simply write: #include "hello.h"
target_include_directories(main PRIVATE
    hello
)

# target_compile_options() adds extra compilation options.
# -Wall and -Wextra enable common warnings that help catch bugs.
target_compile_options(main PRIVATE
    -Wall -Wextra
)
# -----------------------------------------------------------------------------
# 7. Adding new folders (example)
# -----------------------------------------------------------------------------
# If you create another folder (e.g., "utils") with additional sources,
# simply extend the configuration like this:
#
# add_executable(main
#     main.c
#     hello/hello.c
#     utils/utils.c       # <- new source file
# )
#
# target_include_directories(main PRIVATE
#     hello
#     utils               # <- add new include folder
# )
#
# This way you can keep your project modular and well-structured.