#------------------------------------------------------------------------------#
# Distributed under the OSI-approved Apache License, Version 2.0.  See
# accompanying file Copyright.txt for details.
#------------------------------------------------------------------------------#

if(ADIOS2_HAVE_MPI AND HDF5_IS_PARALLEL)
  set(hdf5_mpi TRUE)
  add_definitions(-DTEST_HDF5_MPI)
else()
  set(hdf5_mpi FALSE)
endif()

gtest_add_tests_helper(WriteReadAsStream ${hdf5_mpi} HDF5 Engine.HDF5. "")
gtest_add_tests_helper(StreamWriteReadHighLevelAPI ${hdf5_mpi}
  HDF5 Engine.HDF5. ""
)
gtest_add_tests_helper(WriteReadAttributesADIOS2 ${hdf5_mpi}
  HDF5 Engine.HDF5. ""
)
gtest_add_tests_helper(WriteMemorySelectionRead  ${hdf5_mpi}
  HDF5 Engine.HDF5. ""
)

gtest_add_tests_helper(NativeHDF5WriteRead ${hdf5_mpi} "" Engine.HDF5. "")
if(HDF5_C_INCLUDE_DIRS)
  target_include_directories(Test.Engine.HDF5.NativeHDF5WriteRead
    PRIVATE ${HDF5_C_INCLUDE_DIRS}
  )
else()
  target_include_directories(Test.Engine.HDF5.NativeHDF5WriteRead
    PRIVATE ${HDF5_INCLUDE_DIRS}
  )
endif()
target_link_libraries(Test.Engine.HDF5.NativeHDF5WriteRead ${HDF5_C_LIBRARIES})
