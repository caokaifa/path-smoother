cmake_minimum_required(VERSION 3.5)
project(path_smoother)

add_compile_options(-std=c++11)

find_package(OpenCV REQUIRED core highgui imgproc imgcodecs)
include_directories(${OpenCV_INCLUDE_DIRS})



add_library(${PROJECT_NAME}
        bucket_queue.h
        math_utils.h
        pose2d.h
        vec2d.h
        vec2i.h

        constants.h
    
        path_smoother.h

        bucket_queue.cpp
        vec2d.cpp

   
        path_smoother.cpp
        )

target_link_libraries(${PROJECT_NAME} ${OpenCV_LIBS})

add_executable(path_smoother_example path_smoother_example.cpp)
target_link_libraries(path_smoother_example ${PROJECT_NAME} ${OpenCV_LIBS})

#add_executable(generate_lane_curves example/generate_lane_curves.cpp)
#target_link_libraries(generate_lane_curves ${PROJECT_NAME} ${OpenCV_LIBS})

