cmake_minimum_required(VERSION 3.5)
project(ReachabilityAnalyzer)
set(CMAKE_CXX_STANDARD 11)

find_package(drake REQUIRED)
find_package(gflags REQUIRED)

find_package(Eigen3 REQUIRED)
include_directories(${Eigen3_INCLUDE_DIR})

find_package(VTK REQUIRED)
include_directories(${VTK_INCLUDE_DIRS})

link_directories(${CMAKE_INSTALL_PREFIX}/lib)

add_executable(reachability_analyzer reachability_analyzer.cpp reachability_analyzer.hpp)
target_link_libraries(reachability_analyzer
    z
    pthread
    ${drake_LIBRARIES}
    ${gflags_LIBRARIES}
    ${VTK_LIBRARIES}
    RemoteTreeViewerWrapper)

install(TARGETS reachability_analyzer DESTINATION bin)
