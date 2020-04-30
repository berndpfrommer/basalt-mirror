cmake_minimum_required(VERSION 3.10)

include("thirdparty/basalt-headers/cmake_modules/PreProjectWorkarounds.cmake")

project(basalt)

if(DEFINED ENV{ROS_VERSION})
  if($ENV{ROS_VERSION} EQUAL "2")
    unset(CATKIN_INSTALL_INTO_PREFIX_ROOT)
    include(${CMAKE_CURRENT_SOURCE_DIR}/CMakeListsROS2.txt)
  elseif($ENV{ROS_VERSION} EQUAL "1")
    include(${CMAKE_CURRENT_SOURCE_DIR}/CMakeListsROS1.txt)
  else()
    message(ERROR "invalid ROS_VERSION environment variable: $ENV{ROS_VERSION}")
  endif()
else()
   message(ERROR "ROS_VERSION environment variable is not set!")
endif()
