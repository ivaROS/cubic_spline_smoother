cmake_minimum_required(VERSION 2.8.3)
project(cubic_spline_smoother)

## Compile as C++11, supported in ROS Kinetic and newer
add_compile_options(-Wall -std=c++14)

find_package(catkin REQUIRED COMPONENTS
    geometry_msgs
)

catkin_package(
  INCLUDE_DIRS include
  LIBRARIES cubic_spline_smoother
#   CATKIN_DEPENDS  
  #DEPENDS 
)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_library(cubic_spline_smoother src/cubic_spline_interpolator.cpp)
target_link_libraries(cubic_spline_smoother
  ${Boost_LIBRARIES}
  ${catkin_LIBRARIES}
)
add_dependencies(cubic_spline_smoother ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})