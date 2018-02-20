cmake_minimum_required(VERSION 3.9)

# my mirtk seems to be missing PointSet ... strange
find_package(MIRTK REQUIRED
	Common 
	Numerics 
	IO 
	Image 
	Transformation 
	Registration)

project(flip)
include_directories("${MIRTK_INCLUDE_DIRS}")
add_executable(flip flip.cc)
target_link_libraries(flip Mirtk::Common)

install(TARGETS flip DESTINATION bin)
