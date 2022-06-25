add_executable(main.o main.cpp)

add_subdirectory(operations)

target_link_libraries(main.o
  PRIVATE
    operations
  )