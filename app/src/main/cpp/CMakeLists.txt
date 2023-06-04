# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.22.1)

# Declares and names the project.

project("avplayer")

add_library( # Sets the name of the library.
        avplayer

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        native-lib.cpp)

include_directories(src/main/cpp/include)
set(my_lib_path  ${CMAKE_SOURCE_DIR}/libs/${ANDROID_ABI})
find_library( # Sets the name of the path variable.
        log-lib

        # Specifies the name of the NDK library that
        # you want CMake to locate.
        log)

target_link_libraries( # Specifies the target library.
        avplayer

        # Links the target library to the log library
        # included in the NDK.
        ${log-lib})