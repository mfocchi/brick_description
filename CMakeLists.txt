######################
# set up the project #
######################
cmake_minimum_required(VERSION 2.8.3)
project(brick_description)


# required to use std::shared_ptr in code AND to link the DG plugins
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wl,--no-as-needed")


############################
# Search for dependencies. #
############################

# find dependencies using catkin

find_package(catkin REQUIRED
  COMPONENTS
)
catkin_package(
  CATKIN_DEPENDS
)


install(DIRECTORY launch/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/launch
  PATTERN ".svn" EXCLUDE)


install(DIRECTORY meshes/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/meshes
  PATTERN ".svn" EXCLUDE)


install(DIRECTORY urdf/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/urdf
  PATTERN ".svn" EXCLUDE)



install(DIRECTORY rviz/
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/rviz
  PATTERN ".svn" EXCLUDE)

catkin_install_python(PROGRAMS scripts/spawnModel.py
    DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

