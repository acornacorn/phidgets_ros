add_executable(interface_kit interface_kit.cpp)
add_dependencies(interface_kit phidgets)

target_link_libraries(interface_kit
	phidget21
	#yaml-cpp
	${catkin_LIBRARIES}
	#${PC_LIBUSB_LIBRARIES}
)

install(TARGETS interface_kit
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

