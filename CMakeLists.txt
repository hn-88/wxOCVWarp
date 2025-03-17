cmake_minimum_required(VERSION 3.2)
cmake_policy(SET CMP0037 NEW)
PROJECT(hello)

set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake_modules/")

# copy-pasting from https://github.com/hn-88/pan2fulldome/blob/main/CMakeLists.txt
# to build only OCVWarp, nothing else.
#find_package(OpenCV REQUIRED)

# #include_directories(~/OpenCVLocal/include/opencv4)
# include_directories(${OpenCV_INCLUDE_DIRS})
# add_executable(OCVWarp.bin OCVWarp.cpp tinyfiledialogs.c)
# target_link_libraries(OCVWarp.bin ${OpenCV_LIBS})

# https://docs.wxwidgets.org/3.2.6/overview_cmake.html#cmake_apps
find_package(wxWidgets REQUIRED COMPONENTS net core base)
if(wxWidgets_USE_FILE) # not defined in CONFIG mode
    include(${wxWidgets_USE_FILE})
endif()
add_executable(OCVWarp.bin hello.cpp)
target_link_libraries(OCVWarp.bin ${wxWidgets_LIBRARIES})
