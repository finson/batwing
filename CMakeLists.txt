message(STATUS "Executing " ${CMAKE_CURRENT_LIST_FILE})

# This CMakeLists.txt file goes in the top level project directory, above the
# source directory and everything else.  Its primary purpose is to correctly
# set the variables needed to cross compile and load to an AVR-based Arduino.

cmake_minimum_required(VERSION 3.5)

# This line is needed only if you use boards with selectable cpu (like mega,
# pro etc) and this line should go before call to "cmake/ArduinoToolchain.cmake"
# This is a dirty hack and should be fixed sometime, because it should go to
# particular cmake subdirectory.

# set(ARDUINO_CPU 16MHzatmega328)

set(CMAKE_TOOLCHAIN_FILE cmake/ArduinoToolchain.cmake)

project(BLINKER C CXX)
set(${PROJECT_NAME}_BOARD uno)

#print_board_list()
#print_programmer_list()

# add system libraries to project
link_directories(${ARDUINO_SDK}/libraries)

# add the project source directory into build
add_subdirectory(src/main/Blink)
