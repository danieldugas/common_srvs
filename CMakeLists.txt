cmake_minimum_required(VERSION 2.8.3)
project(common_srvs)

set(MESSAGE_DEPS
  std_msgs)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS genmsg message_generation ${MESSAGE_DEPS})

# Find all the service files
FILE(GLOB SRV_FILES RELATIVE "${CMAKE_CURRENT_SOURCE_DIR}/srv"
      "${CMAKE_CURRENT_SOURCE_DIR}/srv/*.srv")

## Generate messages in the 'srv' folder
add_service_files(
  FILES
  ${SRV_FILES}
)

## Generate added messages and services with any dependencies listed here
generate_messages(
   DEPENDENCIES
   ${MESSAGE_DEPS}
)

catkin_package(
  CATKIN_DEPENDS genmsg message_runtime ${MESSAGE_DEPS}
)


