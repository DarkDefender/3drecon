cmake_minimum_required(VERSION 2.6 FATAL_ERROR)

project( OpenCVReprojectImageToPointCloud )

if(APPLE)
	link_directories(/usr/local/opt/opencv3/share/OpenCV/3rdparty/lib/ /usr/local/opt/opencv3/lib)
endif()

set(PCL_DIR "/cygdrive/d/PCL-1.5.1/cmake")
set(PCL_ROOT "/cygdrive/d/PCL-1.5.1")

include(FindPkgConfig)
pkg_search_module(OPENCV REQUIRED opencv)
find_package( PCL 1.2 REQUIRED )

include_directories(SYSTEM ${OPENCV_INCLUDE_DIRS} ${PCL_INCLUDE_DIRS})
#include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

#find_package( OpenCV REQUIRED )
add_executable( disp2cloud opencv_reproject_image_pcl.cpp )
target_link_libraries( disp2cloud ${OPENCV_LIBRARIES} ${PCL_LIBRARIES})

