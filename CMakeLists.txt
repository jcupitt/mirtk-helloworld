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
add_executable(flip flip.cc)
include_directories("${MIRTK_INCLUDE_DIRS}")
target_link_libraries(flip mirtk::LibCommon)

install(TARGETS flip DESTINATION bin)
