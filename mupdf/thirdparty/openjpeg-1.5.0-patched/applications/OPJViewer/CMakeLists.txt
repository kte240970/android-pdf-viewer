PROJECT(viewer CXX)

FIND_PACKAGE(wxWidgets REQUIRED)
INCLUDE(${wxWidgets_USE_FILE})

INCLUDE_DIRECTORIES(
  ${CMAKE_CURRENT_SOURCE_DIR}/../..
  ${CMAKE_CURRENT_SOURCE_DIR}/..
  )

# original flags:
# -DUSE_JPWL -DwxUSE_LIBOPENJPEG -DwxUSE_GUI=1 -DOPJ_STATIC -DOPJ_HTMLABOUT -DOPJ_INICONFIG -DUSE_JPSEC -DOPJ_MANYFORMATS
ADD_DEFINITIONS(-DwxUSE_LIBOPENJPEG -DOPENJPEG_VERSION="1.5.0")
SET(OPJV_SRCS
  ${CMAKE_CURRENT_SOURCE_DIR}/source/imagjpeg2000.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/source/wxj2kparser.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/source/OPJViewer.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/source/wxjp2parser.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/source/OPJDialogs.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/source/OPJThreads.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/source/OPJAbout.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/../codec/index.c
  )
ADD_EXECUTABLE(opjviewer ${OPJV_SRCS})
TARGET_LINK_LIBRARIES(opjviewer ${wxWidgets_LIBRARIES} openjpeg)
