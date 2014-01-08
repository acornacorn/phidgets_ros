cmake_minimum_required(VERSION 2.8.3)
project(phidgets)

if(NOT CMAKE_CONFIGURATION_TYPES AND NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release)
endif()

find_package(catkin REQUIRED COMPONENTS roscpp genmsg)

# include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})

find_package(PkgConfig)
pkg_check_modules(PC_LIBUSB REQUIRED libusb-1.0)

add_message_files(
  FILES
  interface_kit_params.msg
)

add_service_files(
  DIRECTORY srv 
  FILES
  interface_kit.srv
)

## Generate added messages and services with any dependencies listed here
 generate_messages(
   DEPENDENCIES
   std_msgs
 )

catkin_package(
	INCLUDE_DIRS include
    LIBRARIES phidgets 
)
include_directories(include
                    ${catkin_INCLUDE_DIRS} 
                    )

link_directories(${catkin_LIBRARY_DIRS})


add_subdirectory(src)

install(DIRECTORY include/ DESTINATION include)

install(DIRECTORY launch DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
install(DIRECTORY config DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION})
