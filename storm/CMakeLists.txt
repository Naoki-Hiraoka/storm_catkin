cmake_minimum_required(VERSION 2.8.12)
project(storm)

set(CMAKE_BUILD_TYPE Release)

find_package(catkin REQUIRED COMPONENTS
  )

include(ExternalProject)

execute_process(COMMAND
  git config --global http.sslVerify false)

ExternalProject_Add(
  storm
  GIT_REPOSITORY https://github.com/Naoki-Hiraoka/storm
  GIT_TAG fix-for-large-model
  CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${CMAKE_INSTALL_PREFIX} -DCMAKE_BUILD_TYPE=Release
  )
