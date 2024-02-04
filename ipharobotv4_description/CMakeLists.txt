cmake_minimum_required(VERSION 3.0.2)
project(ipharobotv4_description)


find_package(catkin REQUIRED COMPONENTS
  urdf
  xacro
)
catkin_package()


###########
## Build ##
###########

include_directories(include ipharobotv4_description
  ${catkin_INCLUDE_DIRS}
)

#############
## Install ##
#############

install(DIRECTORY meshes rviz urdf
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION}
)

#############
## Testing ##
#############
