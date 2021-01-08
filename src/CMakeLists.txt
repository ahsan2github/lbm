set(lib_target lbmlib)
set(binary_app lbm)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

file(GLOB CPP *.cpp)
file(GLOB SRCHEADERS ${CMAKE_SOURCE_DIR}/src/*.h)
add_library(${lib_target} STATIC ${CPP} ${SRCHEADERS})
set_target_properties(${lib_target} 
                      PROPERTIES 
                      CXX_STANDARD 17)
target_compile_options(${lib_target} PUBLIC "--verbose")

add_executable(${binary_app} launcher.cpp)
target_link_libraries(${binary_app} ${lib_target})
set_target_properties(${binary_app} 
                      PROPERTIES 
                      CXX_STANDARD 17)
