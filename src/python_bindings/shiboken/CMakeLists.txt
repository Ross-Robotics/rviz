# Build file for Python bindings via shiboken and pyside.

set(rviz_shiboken_QT_COMPONENTS
  QtCore
  QtGui
)


list(APPEND CMAKE_MODULE_PATH /home/jj/.local/lib/python2.7/site-packages)
list(APPEND CMAKE_MODULE_PATH /usr/lib)
message(WARNING "CMAKE_MODULE_PATH: ${CMAKE_MODULE_PATH}")

set(PYTHON_EXTENSION_SUFFIX "${PYTHON_SUFFIX}-${CMAKE_CXX_LIBRARY_ARCHITECTURE}")
message(WARNING "PYTHON_EXTENSION_SUFFIX: ${PYTHON_EXTENSION_SUFFIX}")
find_package(Shiboken2)

set(PYTHON_EXTENSION_SUFFIX "${PYTHON_SUFFIX}")
message(WARNING "PYTHON_EXTENSION_SUFFIX: ${PYTHON_EXTENSION_SUFFIX}")
find_package(Shiboken2)

set(PYTHON_EXTENSION_SUFFIX "")
message(WARNING "PYTHON_EXTENSION_SUFFIX: ${PYTHON_EXTENSION_SUFFIX}")
find_package(Shiboken2)


set(PYTHON_EXTENSION_SUFFIX "")
message(WARNING "PYTHON_EXTENSION_SUFFIX: ${PYTHON_EXTENSION_SUFFIX}")
find_package(Shiboken2)

# #catkin_lint: ignore_once duplicate_find
# find_package(python_qt_binding REQUIRED)
# include(${python_qt_binding_EXTRAS_DIR}/shiboken_helper.cmake)
# message(WARNING "found: ${PYTHON_EXTENSION_SUFFIX}")
# # /home/jj/.local/lib/python2.7/site-packages
# message(WARNING "Entered this file")
# include(find_shiboken2.cmake)



# find_package(Shiboken2)
# if(Shiboken2_FOUND)
# message(WARNING "found: Shiboken2_FOUND")
# endif()
# find_package(PySide2)
# if(PySide2_FOUND)
# message(WARNING "found: PySide2_FOUND")
# endif()
# find_package(PythonLibs "${PYTHON_VERSION_MAJOR}.${PYTHON_VERSION_MINOR}")
# if(PYTHONLIBS_FOUND)
# message(WARNING "found: PYTHONLIBS_FOUND")
# endif()



# if(shiboken_helper_FOUND)
# message(WARNING "Thing is found: ${shiboken_helper_FOUND}")
#   set(_configure_shiboken TRUE)
#   if(Shiboken_VERSION VERSION_GREATER "1.1.1")
#   message(WARNING "Thing is Shiboken_VERSION: ${Shiboken_VERSION}")
#     if(APPLE AND Shiboken_VERSION VERSION_GREATER "1.2.1")
#       # This appears to no longer be a problem at least with Shiboken 1.2.2 on OS X and Boost 1.57.
#       set(_configure_shiboken TRUE)
#     else()
#       # shiboken 1.1.2 and higher will segfault until https://bugreports.qt-project.org/browse/PYSIDE-218 is fixed
#       #set(_configure_shiboken FALSE)
#       message(WARNING "Shiboken version ${Shiboken_VERSION} would segfault when trying to process rviz (see https://bugreports.qt-project.org/browse/PYSIDE-218). Therefore shiboken bindings are being skipped.")
#     endif()
#   endif()
#   message(WARNING "Gonna dO is _configure_shiboken: ${_configure_shiboken}")
#   if(_configure_shiboken)
#     list(APPEND rviz_BINDINGS "shiboken")
#     set(rviz_BINDINGS "${rviz_BINDINGS}" PARENT_SCOPE)

#     # To add a new rviz class to the bindings, add it:
#     # - in rviz_shiboken_SRCS below, like rviz_myclass_wrapper.cpp
#     # - in rviz_HDRS below, like ../rviz/my_class.h
#     # - in global.h, like #include <rviz/my_class.h>
#     # - in typesystem.xml, like <object-type name="rviz::MyClass"/>

#     set(rviz_shiboken_SRCS
#       librviz_shiboken/librviz_shiboken_module_wrapper.cpp
#       librviz_shiboken/rviz_visualizationframe_wrapper.cpp
#       librviz_shiboken/rviz_visualizationmanager_wrapper.cpp
#       librviz_shiboken/rviz_display_wrapper.cpp
#       librviz_shiboken/rviz_displaygroup_wrapper.cpp
#       librviz_shiboken/rviz_ogrelogging_wrapper.cpp
#       librviz_shiboken/rviz_property_wrapper.cpp
#       librviz_shiboken/rviz_boolproperty_wrapper.cpp
#       librviz_shiboken/rviz_paneldockwidget_wrapper.cpp
#       librviz_shiboken/rviz_viewmanager_wrapper.cpp
#       librviz_shiboken/rviz_viewcontroller_wrapper.cpp
#       librviz_shiboken/rviz_tool_wrapper.cpp
#       librviz_shiboken/rviz_toolmanager_wrapper.cpp
#       librviz_shiboken/rviz_config_wrapper.cpp
#       librviz_shiboken/rviz_config_mapiterator_wrapper.cpp
#       librviz_shiboken/rviz_yamlconfigreader_wrapper.cpp
#       librviz_shiboken/rviz_yamlconfigwriter_wrapper.cpp
#       librviz_shiboken/rviz_wrapper.cpp
#     )

#     set(rviz_shiboken_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/src)

#     set(rviz_HDRS
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/visualization_frame.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/visualization_manager.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/view_manager.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/view_controller.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/display.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/display_group.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/properties/property.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/properties/bool_property.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/panel_dock_widget.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/tool.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/tool_manager.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/ogre_helpers/ogre_logging.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/config.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/yaml_config_reader.h
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/yaml_config_writer.h
#     )

#     shiboken_generator(
#       librviz
#       global.h
#       typesystem.xml
#       ${PROJECT_SOURCE_DIR}/src/python_bindings/shiboken
#       "${rviz_shiboken_SRCS}"
#       "${rviz_HDRS}"
#       "${rviz_shiboken_INCLUDE_DIR}"
#       "${CMAKE_CURRENT_BINARY_DIR}"
#     )

#     include_directories(rviz_shiboken
#       ${rviz_shiboken_INCLUDE_DIR}/rviz
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/properties
#       ${rviz_shiboken_INCLUDE_DIR}/rviz/ogre_helpers
#     )
#     shiboken_include_directories(rviz_shiboken "${rviz_shiboken_QT_COMPONENTS}")
#     add_library(rviz_shiboken ${rviz_shiboken_SRCS})
#     if(NOT WIN32)
#       set_target_properties(rviz_shiboken PROPERTIES COMPILE_FLAGS "-std=c++11")
#     endif()
#     set_target_properties(rviz_shiboken PROPERTIES
#       LIBRARY_OUTPUT_DIRECTORY ${CATKIN_DEVEL_PREFIX}/${PYTHON_INSTALL_DIR}/rviz)
#     target_link_libraries(rviz_shiboken ${PROJECT_NAME})
#     shiboken_target_link_libraries(rviz_shiboken "${rviz_shiboken_QT_COMPONENTS}")

#     install(TARGETS rviz_shiboken
#       LIBRARY DESTINATION ${CATKIN_PACKAGE_PYTHON_DESTINATION})
#   endif()
# endif()
