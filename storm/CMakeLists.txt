cmake_minimum_required(VERSION 2.8.12)
project(storm)

set(CMAKE_BUILD_TYPE Release)

find_package(catkin REQUIRED COMPONENTS
  )

include(ExternalProject)

execute_process(COMMAND
  git config --global http.sslVerify false)

if("$ENV{ROS_DISTRO}" STRGREATER "melodic")
  set(STORM_TAG fix-for-large-model20)
else()
  set(STORM_TAG fix-for-large-model)
endif()

ExternalProject_Add(
  storm
  GIT_REPOSITORY https://github.com/Naoki-Hiraoka/storm
  GIT_TAG ${STORM_TAG}
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX} -DCMAKE_BUILD_TYPE=Release
  )
