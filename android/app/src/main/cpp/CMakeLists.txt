cmake_minimum_required(VERSION 3.22.1)

project("chili3dnative")

# Add sources from the existing cpp directory
# Adjust the path as necessary if the subtask runs from a different working directory
file(GLOB_RECURSE CPP_SOURCES "../../../cpp/src/*.cpp")

add_library( # Sets the name of the library.
             chili3dnative

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             native-lib.cpp
             ${CPP_SOURCES} )

# Link against Android log library
find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

target_link_libraries( # Specifies the target library.
                       chili3dnative

                       # Links the target library to the log library
                       # specified by the path variable log-lib.
                       ${log-lib} )
