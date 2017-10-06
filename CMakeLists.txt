cmake_minimum_required(VERSION 2.8.12)

project(dart-planning)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/cmake")

#===============================================================================
# Dependencies
#===============================================================================
find_package(DART 6.3 REQUIRED COMPONENTS utils)
find_package(FLANN 1.8.4 REQUIRED)

#===============================================================================
# Library
#===============================================================================
set(headers
  dart/planning/Path.hpp
  dart/planning/PathFollowingTrajectory.hpp
  dart/planning/PathPlanner.hpp
  dart/planning/PathShortener.hpp
  dart/planning/RRT.hpp
  dart/planning/Trajectory.hpp
)

set(sources
  dart/planning/Path.cpp
  dart/planning/PathFollowingTrajectory.cpp
  dart/planning/PathShortener.cpp
  dart/planning/RRT.cpp
)

add_library(dart-planning ${headers} ${sources})
target_link_libraries(dart-planning PUBLIC
  ${DART_LIBRARIES}
  ${FLANN_LIBRARIES}
)
