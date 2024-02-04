cmake_minimum_required(VERSION 3.0.2)
project(ipharobotv4_bootstrap)

add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  diagnostic_msgs
  roscpp
  sensor_msgs
  std_msgs
  ipharobotv4_msgs
)

catkin_package()

include_directories(
  include
  ${catkin_INCLUDE_DIRS}
)

add_executable(ipharobotv4_diagnostics src/ipharobotv4_diagnostics.cpp)
add_dependencies(ipharobotv4_diagnostics ${ipharobotv4_diagnostics_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
target_link_libraries(ipharobotv4_diagnostics ${catkin_LIBRARIES})


install(TARGETS ipharobotv4_diagnostics
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(PROGRAMS 
  scripts/create_udev_rules
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

install(FILES 99-ipharobot-cdc.rules
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)


