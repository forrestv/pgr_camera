# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)
project(pgr_camera)
# Load catkin and all dependencies required for this package
# TODO: remove all from COMPONENTS that are not catkin packages.
find_package(catkin REQUIRED COMPONENTS self_test dynamic_reconfigure roscpp driver_base std_msgs camera_info_manager sensor_msgs image_transport diagnostic_updater diagnostic_msgs)
# CATKIN_MIGRATION: removed during catkin migration
# cmake_minimum_required(VERSION 2.4.6)

# CATKIN_MIGRATION: removed during catkin migration
# include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)


# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_init()

#set the default path for built executables to the "bin" directory

# CATKIN_MIGRATION: removed during catkin migration
# set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory

# CATKIN_MIGRATION: removed during catkin migration
# set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)


# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_add_boost_directories()

# Generate dynamic parameters

# CATKIN_MIGRATION: removed during catkin migration
# rosbuild_find_ros_package(dynamic_reconfigure)

# CATKIN_MIGRATION: removed during catkin migration
# include(${dynamic_reconfigure_PACKAGE_PATH}/cmake/cfgbuild.cmake)
generate_dynamic_reconfigure_options(
  cfg/PGRCamera.cfg
)
## Generate added messages and services with any dependencies listed here
#generate_messages(
#    DEPENDENCIES 
#)

# catkin_package parameters: http://ros.org/doc/groovy/api/catkin/html/dev_guide/generated_cmake_api.html#catkin-package
# TODO: fill in what other packages will need to use this package
catkin_package(
    DEPENDS  # TODO
    CATKIN_DEPENDS self_test dynamic_reconfigure roscpp driver_base std_msgs camera_info_manager sensor_msgs image_transport diagnostic_updater diagnostic_msgs
    INCLUDE_DIRS include# TODO include
    LIBRARIES # TODO
)

include_directories(include ${Boost_INCLUDE_DIR} ${catkin_INCLUDE_DIRS})


#uncomment if you have defined messages
#rosbuild_genmsg()
#uncomment if you have defined services
#rosbuild_gensrv()

#common commands for building c++ executables and libraries
#rosbuild_add_library(${PROJECT_NAME} src/example.cpp)
#target_link_libraries(${PROJECT_NAME} another_library)
#rosbuild_add_boost_directories()
#rosbuild_link_boost(${PROJECT_NAME} thread)
#rosbuild_add_executable(example examples/example.cpp)
#target_link_libraries(example ${PROJECT_NAME})
add_subdirectory(src)
#rosbuild_add_executable(pgr_camera_node src/pgr_camera_node.cpp)
