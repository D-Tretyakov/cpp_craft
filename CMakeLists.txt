cmake_minimum_required(VERSION 3.25)

project(CppCraft)

set(CMAKE_CXX_STANDARD 17)

set(VULKAN_PATH "C:/VulkanSDK/1.3.236.0")
set(ENV{VULKAN_SDK} ${VULKAN_PATH})
find_package(Vulkan REQUIRED)

add_executable(${PROJECT_NAME} main.cpp)

target_link_libraries(${PROJECT_NAME} ${Vulkan_LIBRARIES})
target_include_directories(${PROJECT_NAME} PUBLIC "${VULKAN_PATH}/Include") 