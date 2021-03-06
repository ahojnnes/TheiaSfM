# Basic programs
ADD_EXECUTABLE(match_descriptors match_descriptors.cc)
TARGET_LINK_LIBRARIES(match_descriptors theia ${GFLAGS_LIBRARIES})

ADD_EXECUTABLE(extract_features extract_features.cc)
TARGET_LINK_LIBRARIES(extract_features theia ${GFLAGS_LIBRARIES})

ADD_EXECUTABLE(compute_two_view_geometry compute_two_view_geometry.cc)
TARGET_LINK_LIBRARIES(compute_two_view_geometry theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

# Tools for building SfM models
ADD_EXECUTABLE(build_reconstruction build_reconstruction.cc)
TARGET_LINK_LIBRARIES(build_reconstruction theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

ADD_EXECUTABLE(build_1dsfm_reconstruction build_1dsfm_reconstruction.cc)
TARGET_LINK_LIBRARIES(build_1dsfm_reconstruction theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

# Reconstruction visualization.
find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
include_directories( ${OPENGL_INCLUDE_DIRS}  ${GLUT_INCLUDE_DIRS} )

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wno-deprecated-declarations")
ADD_EXECUTABLE(view_reconstruction view_reconstruction.cc)
TARGET_LINK_LIBRARIES(view_reconstruction theia ${GFLAGS_LIBRARIES}
  ${OPENGL_LIBRARIES}
  ${GLUT_LIBRARY})

# Useful tools for analyzing reconstructions.
ADD_EXECUTABLE(compute_reconstruction_statistics compute_reconstruction_statistics.cc)
TARGET_LINK_LIBRARIES(compute_reconstruction_statistics theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

ADD_EXECUTABLE(compare_reconstructions compare_reconstructions.cc)
TARGET_LINK_LIBRARIES(compare_reconstructions theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

ADD_EXECUTABLE(compute_matching_relative_pose_errors compute_matching_relative_pose_errors.cc)
TARGET_LINK_LIBRARIES(compute_matching_relative_pose_errors theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

ADD_EXECUTABLE(verify_1dsfm_input verify_1dsfm_input.cc)
TARGET_LINK_LIBRARIES(verify_1dsfm_input theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

# File conversions and exporters.
ADD_EXECUTABLE(convert_sift_key_file convert_sift_key_file.cc)
TARGET_LINK_LIBRARIES(convert_sift_key_file theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

ADD_EXECUTABLE(convert_bundle_file convert_bundle_file.cc)
TARGET_LINK_LIBRARIES(convert_bundle_file theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

ADD_EXECUTABLE(write_reconstruction_ply_file write_reconstruction_ply_file.cc)
TARGET_LINK_LIBRARIES(write_reconstruction_ply_file theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})

ADD_EXECUTABLE(export_reconstruction_to_pmvs export_reconstruction_to_pmvs.cc)
TARGET_LINK_LIBRARIES(export_reconstruction_to_pmvs theia ${GFLAGS_LIBRARIES} ${GLOG_LIBRARIES})
