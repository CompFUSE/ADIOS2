message_start_thirdparty()

set(BUILD_TESTING OFF)
set(CMAKE_INSTALL_CMAKEDIR "${CMAKE_INSTALL_CMAKEDIR}/thirdparty")

set(EVPATH_LIBRARY_PREFIX adios2_ CACHE INTERNAL "")
set(EVPATH_QUIET ON CACHE INTERNAL "")
set(EVPATH_INSTALL_HEADERS OFF CACHE INTERNAL "")
set(EVPATH_INSTALL_PKGCONFIG OFF CACHE INTERNAL "")
set(EVPATH_NO_RDMA ON CACHE INTERNAL "")
set(EVPATH_USE_UDT4 OFF CACHE INTERNAL "")
set(EVPATH_USE_NVML OFF CACHE INTERNAL "")
set(EVPATH_DEFAULT_PORT_RANGE "ANY" CACHE INTERNAL "")

add_subdirectory(EVPath)
set(EVPath_DIR ${CMAKE_CURRENT_BINARY_DIR}/EVPath CACHE INTERNAL "")

message_end_thirdparty()
