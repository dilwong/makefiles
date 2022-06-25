add_library(operations "")

target_sources(operations
  PRIVATE
    add.cpp
  PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}/add.hpp
  )

target_include_directories(operations
  PUBLIC
    ${CMAKE_CURRENT_LIST_DIR}
  )