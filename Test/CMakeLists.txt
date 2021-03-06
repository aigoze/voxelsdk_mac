SET(VOXEL_TEST_VERSION ${VOXEL_VERSION})

add_executable(DeviceTest DeviceTest.cpp)
target_link_libraries(DeviceTest voxel)

add_executable(DownloaderTest DownloaderTest.cpp)
target_link_libraries(DownloaderTest voxel)

add_executable(CameraSystemTest CameraSystemTest.cpp)
target_link_libraries(CameraSystemTest voxel)

add_executable(CameraSystemConfigTest CameraSystemConfigTest.cpp)
target_link_libraries(CameraSystemConfigTest voxel)

add_executable(CameraSystemSaveStreamTest CameraSystemSaveStreamTest.cpp)
target_link_libraries(CameraSystemSaveStreamTest voxel)

add_executable(CameraSystemReadStreamTest CameraSystemReadStreamTest.cpp)
target_link_libraries(CameraSystemReadStreamTest voxel)

add_executable(DMLParseTest DMLParseTest.cpp)
target_link_libraries(DMLParseTest voxel)

add_executable(Data2DCodecTest Data2DCodecTest.cpp)
target_link_libraries(Data2DCodecTest voxel)

add_executable(DFTTest DFTTest.cpp)
target_link_libraries(DFTTest voxel)

install(TARGETS
  DeviceTest 
  DownloaderTest 
  CameraSystemTest
  CameraSystemConfigTest
  CameraSystemSaveStreamTest
  CameraSystemReadStreamTest
  DMLParseTest
  Data2DCodecTest
  DFTTest
  RUNTIME
  DESTINATION bin
  COMPONENT test
)
             
IF(LINUX)
  set(CPACK_COMPONENTS_ALL test)
  set(CPACK_PACKAGE_DESCRIPTION_SUMMARY "Voxel library test programs.")
  set(CPACK_DEBIAN_PACKAGE_DEPENDS "libvoxel (>= ${VOXEL_VERSION})")
  create_cpack_config(libvoxel-test ${VOXEL_TEST_VERSION})
ENDIF()
