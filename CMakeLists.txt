cmake_minimum_required(VERSION 3.5)
project(socks)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(Threads REQUIRED)
# find_package(asio REQUIRED)

message("++++++++++++++++++++++++++++++++++++++++++++++++++++++")
message(INFO ${CMAKE_CURRENT_SOURCE_DIR})
message("++++++++++++++++++++++++++++++++++++++++++++++++++++++")

add_executable(${CMAKE_PROJECT_NAME}_client src/client.cpp)
add_executable(${CMAKE_PROJECT_NAME}_server src/server.cpp)

target_include_directories(${CMAKE_PROJECT_NAME}_client PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include/websocketpp)
target_include_directories(${CMAKE_PROJECT_NAME}_server 
  PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include/websocketpp
  PUBLIC /usr/include/asio
  )

target_link_libraries(${CMAKE_PROJECT_NAME}_client PUBLIC Threads::Threads) #Asio::Asio)
target_link_libraries(${CMAKE_PROJECT_NAME}_server PUBLIC Threads::Threads) #Asio::Asio)

install(TARGETS
  ${CMAKE_PROJECT_NAME}_client
  ${CMAKE_PROJECT_NAME}_server
  DESTINATION lib/${PROJECT_NAME})