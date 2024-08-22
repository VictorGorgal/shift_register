cmake_minimum_required(VERSION 3.10)

project(shift_register)

# Specify the source files
set(SOURCES
    src/shift_register.c
)

# Create the library
add_library(shift_register STATIC ${SOURCES})

pico_generate_pio_header(shift_register
	${CMAKE_CURRENT_LIST_DIR}/src/shift_register.pio
)

# Specify include directories
target_include_directories(shift_register PUBLIC include)

# Link the necessary libraries
target_link_libraries(shift_register
	pico_stdlib
	hardware_pio
)
