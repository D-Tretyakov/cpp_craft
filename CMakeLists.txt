cmake_minimum_required(VERSION 3.25)

project(CppCraft)

set(CMAKE_CXX_STANDARD 17)

set(VULKAN_PATH "C:/VulkanSDK/1.3.236.0")
set(ENV{VULKAN_SDK} ${VULKAN_PATH})
find_package(Vulkan REQUIRED)

find_package(glfw3 3.3 REQUIRED PATHS "C:/Program Files (x86)/GLFW/lib/cmake/glfw3")

# copy shaders into working dir
file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/shaders/vert.spv
     DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/shaders)

file(COPY ${CMAKE_CURRENT_SOURCE_DIR}/shaders/frag.spv
     DESTINATION ${CMAKE_CURRENT_BINARY_DIR}/shaders)

add_executable(${PROJECT_NAME} main.cpp)

target_link_libraries(${PROJECT_NAME} glfw)

target_link_libraries(${PROJECT_NAME} ${Vulkan_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC "${VULKAN_PATH}/Include")
target_link_directories(${PROJECT_NAME} PUBLIC ${VULKAN_PATH}/Bin;${VULKAN_PATH}/Lib;)