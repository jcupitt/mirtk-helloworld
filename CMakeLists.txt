CMAKE_MINIMUM_REQUIRED(VERSION 3.9)

# my mirtk seems to be missing PointSet ... strange
FIND_PACKAGE(MIRTK REQUIRED
	Common 
	Numerics 
	IO 
	Image 
	Transformation 
	Registration)

project(flip)
#include_directories("${MIRTK_INCLUDE_DIRS}")
add_executable(flip flip.cc)
target_link_libraries(flip MIRTK::Common)

install(TARGETS flip DESTINATION bin)
