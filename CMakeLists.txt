cmake_minimum_required(VERSION 3.5)
project(urjc_building_3_world)

find_package(ros_gz_sim REQUIRED)
find_package(ament_cmake_ros REQUIRED)

install(DIRECTORY launch models worlds 
    DESTINATION share/${PROJECT_NAME}
)

ament_environment_hooks("${CMAKE_CURRENT_SOURCE_DIR}/env-hooks/urjc_building_3_world.dsv.in")

ament_export_dependencies(ros_gz_sim)

ament_package()

