set(SUBSYS_NAME tests_gpu_octree)
set(SUBSYS_DESC "Point cloud library gpu octree tests")
set(SUBSYS_DEPS common octree gpu_containers gpu_octree gpu_utils)

PCL_SUBSYS_OPTION(build "${SUBSYS_NAME}" "${SUBSYS_DESC}" ON)
PCL_SUBSYS_DEPEND(build NAME ${SUBSYS_NAME} DEPS ${SUBSYS_DEPS} OPT_DEPS ${OPT_DEPS})

if(NOT build)
  return()
endif()

PCL_ADD_TEST(gpu_octree_performance test_gpu_octree_performance FILES performance.cpp LINK_WITH pcl_gtest pcl_common pcl_octree pcl_gpu_octree)
PCL_ADD_TEST(gpu_octree_approx_nearest test_gpu_approx_nearest FILES test_approx_nearest.cpp LINK_WITH pcl_gtest pcl_common pcl_octree pcl_gpu_octree pcl_gpu_utils)
PCL_ADD_TEST(gpu_octree_bfrs test_gpu_bfrs FILES test_bfrs_gpu.cpp LINK_WITH pcl_gtest pcl_common pcl_octree pcl_gpu_octree)
PCL_ADD_TEST(gpu_octree_host_radius test_gpu_host_radius_search FILES test_host_radius_search.cpp LINK_WITH pcl_gtest pcl_common pcl_octree pcl_gpu_octree)
PCL_ADD_TEST(gpu_octree_knn_search test_gpu_knn_search FILES test_knn_search.cpp LINK_WITH pcl_gtest pcl_common pcl_octree pcl_gpu_octree)
PCL_ADD_TEST(gpu_octree_radius_search test_gpu_radius_search FILES test_radius_search.cpp LINK_WITH pcl_gtest pcl_common pcl_octree pcl_gpu_octree)
