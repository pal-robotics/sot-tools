
# Copyright 2012, CNRS
# Author: Florent Lamiraux
#

CMAKE_MINIMUM_REQUIRED(VERSION 2.8.3)

find_package(catkin REQUIRED COMPONENTS sot_cmake sot-core)

INCLUDE(${SOT_CMAKE_DIR}/base.cmake)
INCLUDE(${SOT_CMAKE_DIR}/cpack.cmake)
INCLUDE(${SOT_CMAKE_DIR}/python.cmake)

FINDPYTHON ()
FIND_NUMPY ()

SET(PROJECT_NAME sot-tools)
SET(PROJECT_DESCRIPTION "Miscellanous entities for the stack of tasks")
SET(PROJECT_URL "http://github.com/laas/sot-tools")

SET(CUSTOM_HEADER_DIR sot/tools)
SET(${PROJECT_NAME}_HEADERS
)

SETUP_PROJECT()
catkin_package()
include_directories(${catkin_INCLUDE_DIRS})

# Trigger dependency to dynamic-graph-python
# Add dependency to libsot-tools.so library in pkg-config file.
PKG_CONFIG_APPEND_LIBS("sot-tools")

ADD_SUBDIRECTORY(src)

SETUP_PROJECT_FINALIZE()
SETUP_PROJECT_CPACK()
