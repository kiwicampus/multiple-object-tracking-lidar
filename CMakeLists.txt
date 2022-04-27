cmake_minimum_required(VERSION 3.5)
project(multi_object_tracking_lidar)

set(CMAKE_CXX_STANDARD 14)

find_package(ament_cmake REQUIRED)
find_package(pcl_ros REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(rclcpp REQUIRED)
find_package( OpenCV REQUIRED )

include_directories(
  ${Boost_INCLUDE_DIRS}
  ${OpenCV_INCLUDE_DIRS}
  include
)

add_executable( kf_tracker src/main.cpp )
target_link_libraries ( kf_tracker ${OpenCV_LIBRARIES} "rclcpp")

install(TARGETS kf_tracker
	ARCHIVE DESTINATION lib
	LIBRARY DESTINATION lib
	RUNTIME DESTINATION bin
)

ament_export_include_directories(include)
ament_package()