cmake_minimum_required(VERSION 3.24)
project(lib)

add_library(lib INTERFACE)

target_sources(
	lib
	INTERFACE
	FILE_SET HEADERS
	TYPE HEADERS
	BASE_DIRS include
	FILES include/my/lib.hpp
)

install(
	TARGETS lib
	FILE_SET HEADERS
	DESTINATION include
)

target_sources(
	lib
	INTERFACE
	FILE_SET visualizers
	TYPE HEADERS
	BASE_DIRS visualizers
	FILES visualizers/my/lib.natvis
)

install(
	TARGETS lib
	FILE_SET visualizers
	DESTINATION visualizers
)

install(
	FILES "${CMAKE_CURRENT_LIST_DIR}/cmake_build_modules/add_visualizers.cmake"
	DESTINATION "cmake_build_modules"
)
