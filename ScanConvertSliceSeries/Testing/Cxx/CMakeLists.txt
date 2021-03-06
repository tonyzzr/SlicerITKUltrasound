
#-----------------------------------------------------------------------------
set(BASELINE ${CMAKE_CURRENT_SOURCE_DIR}/../../Data/Baseline)
set(INPUT ${CMAKE_CURRENT_SOURCE_DIR}/../../Data/Input)
set(TEMP "${CMAKE_BINARY_DIR}/Testing/Temporary")

set(CLP ${MODULE_NAME})

#-----------------------------------------------------------------------------
add_executable(${CLP}Test ${CLP}Test.cxx)
target_link_libraries(${CLP}Test ${CLP}Lib ${SlicerExecutionModel_EXTRA_EXECUTABLE_TARGET_LIBRARIES})
set_target_properties(${CLP}Test PROPERTIES LABELS ${CLP})

#-----------------------------------------------------------------------------
set(testname ${CLP}Test)
ExternalData_add_test(${CLP}Data NAME ${testname} COMMAND
  ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  --compare DATA{${BASELINE}/${CLP}TestOutput.mha}
    ${TEMP}/${CLP}TestOutput.mha
  ModuleEntryPoint
    --outputSpacing 1.0,1.0,1.0
    DATA{${INPUT}/bmode_p59.hdf5}
    ${TEMP}/${CLP}TestOutput.mha
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

set(testname ${CLP}ITKGaussianTest)
ExternalData_add_test(${CLP}Data NAME ${testname} COMMAND
  ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  --compare DATA{${BASELINE}/${CLP}ITKGaussianTestOutput.mha}
    ${TEMP}/${CLP}ITKGaussianTestOutput.mha
  ModuleEntryPoint
    --method ITKGaussian
    --outputSpacing 1.0,1.0,1.0
    DATA{${INPUT}/bmode_p59.hdf5}
    ${TEMP}/${CLP}ITKGaussianTestOutput.mha
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

set(testname ${CLP}VTKProbeFilterTest)
ExternalData_add_test(${CLP}Data NAME ${testname} COMMAND
  ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  --compare DATA{${BASELINE}/${CLP}VTKProbeFilterTestOutput.mha}
    ${TEMP}/${CLP}VTKProbeFilterTestOutput.mha
  ModuleEntryPoint
    --method VTKProbeFilter
    --outputSpacing 1.0,1.0,1.0
    DATA{${INPUT}/bmode_p59.hdf5}
    ${TEMP}/${CLP}VTKProbeFilterTestOutput.mha
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

set(testname ${CLP}VTKGaussianKernelTest)
ExternalData_add_test(${CLP}Data NAME ${testname} COMMAND
  ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  --compare DATA{${BASELINE}/${CLP}VTKGaussianKernelTestOutput.mha}
    ${TEMP}/${CLP}VTKGaussianKernelTestOutput.mha
  ModuleEntryPoint
    --method VTKGaussianKernel
    --outputSpacing 1.0,1.0,1.0
    DATA{${INPUT}/bmode_p59.hdf5}
    ${TEMP}/${CLP}VTKGaussianKernelTestOutput.mha
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

set(testname ${CLP}VTKLinearKernelTest)
ExternalData_add_test(${CLP}Data NAME ${testname} COMMAND
  ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  --compare DATA{${BASELINE}/${CLP}VTKLinearKernelTestOutput.mha}
    ${TEMP}/${CLP}VTKLinearKernelTestOutput.mha
  ModuleEntryPoint
    --method VTKLinearKernel
    --outputSpacing 1.0,1.0,1.0
    DATA{${INPUT}/bmode_p59.hdf5}
    ${TEMP}/${CLP}VTKLinearKernelTestOutput.mha
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

set(testname ${CLP}VTKShepardKernelTest)
ExternalData_add_test(${CLP}Data NAME ${testname} COMMAND
  ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  --compare DATA{${BASELINE}/${CLP}VTKShepardKernelTestOutput.mha}
    ${TEMP}/${CLP}VTKShepardKernelTestOutput.mha
  ModuleEntryPoint
    --method VTKShepardKernel
    --outputSpacing 1.0,1.0,1.0
    DATA{${INPUT}/bmode_p59.hdf5}
    ${TEMP}/${CLP}VTKShepardKernelTestOutput.mha
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

set(testname ${CLP}VTKVoronoiKernelTest)
ExternalData_add_test(${CLP}Data NAME ${testname} COMMAND
  ${SEM_LAUNCH_COMMAND} $<TARGET_FILE:${CLP}Test>
  --compare DATA{${BASELINE}/${CLP}VTKVoronoiKernelTestOutput.mha}
    ${TEMP}/${CLP}VTKVoronoiKernelTestOutput.mha
  ModuleEntryPoint
    --method VTKVoronoiKernel
    --outputSpacing 1.0,1.0,1.0
    DATA{${INPUT}/bmode_p59.hdf5}
    ${TEMP}/${CLP}VTKVoronoiKernelTestOutput.mha
  )
set_property(TEST ${testname} PROPERTY LABELS ${CLP})

#-----------------------------------------------------------------------------
ExternalData_add_target(${CLP}Data)
