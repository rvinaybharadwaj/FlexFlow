cmake_minimum_required(VERSION 3.10)

project(FlexFlowExample_Inception)
set(project_target inception)

set(CPU_SRC
  inception.cc
  inception.h)

set(GPU_SRC
  inception.cu)

cuda_add_executable(${project_target} ${CPU_SRC} ${GPU_SRC})
target_include_directories(${project_target} PRIVATE ${FLEXFLOW_INCLUDE_DIRS} ${CMAKE_INSTALL_INCLUDEDIR})
target_link_libraries(${project_target} -Wl,--whole-archive flexflow ${Legion_LIBRARIES} ${Realm_LIBRARIES} -Wl,--no-whole-archive ${FLEXFLOW_EXT_LIBRARIES})

