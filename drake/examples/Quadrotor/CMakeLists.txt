
if (LCM_FOUND AND NOT WIN32)
  add_executable(runQuadrotorDynamics runDynamics.cpp)
  target_link_libraries(runQuadrotorDynamics drakeRBSystem drakeLCMSystem)
  add_dependencies(runQuadrotorDynamics drake_lcmtypes lcmtype_agg_hpp)
  pods_use_pkg_config_packages(runQuadrotorDynamics lcm)
  add_test(NAME runQuadrotorDynamics COMMAND runQuadrotorDynamics 5.0)

  add_executable(runQuadrotorLQR runLQR.cpp)
  target_link_libraries(runQuadrotorLQR drakeRBM)
  add_dependencies(runQuadrotorLQR drake_lcmtypes lcmtype_agg_hpp)
  pods_use_pkg_config_packages(runQuadrotorLQR lcm)
  add_test(NAME runQuadrotorLQR COMMAND runQuadrotorLQR WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}/examples/Quadrotor)
endif()

add_subdirectory(test)