add_library(phidgets interface_kit.cpp)
add_dependencies(phidgets phidgets_gencpp)

target_link_libraries(phidgets
	phidget21
	#yaml-cpp
	${catkin_LIBRARIES}
	#${PC_LIBUSB_LIBRARIES}
)

install(TARGETS phidgets
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION})

