set(WCSPH_HEADER_FILES
	WCSPH/SimulationDataWCSPH.h
	WCSPH/TimeStepWCSPH.h
	)
	
set(WCSPH_SOURCE_FILES
	WCSPH/SimulationDataWCSPH.cpp
	WCSPH/TimeStepWCSPH.cpp
	)		
	
set(PCISPH_HEADER_FILES
	PCISPH/SimulationDataPCISPH.h
	PCISPH/TimeStepPCISPH.h
	)
	
set(PCISPH_SOURCE_FILES
	PCISPH/SimulationDataPCISPH.cpp
	PCISPH/TimeStepPCISPH.cpp
	)

set(PBF_HEADER_FILES
	PBF/SimulationDataPBF.h
	PBF/TimeStepPBF.h
	PBF/TimeIntegration.h
	)
	
set(PBF_SOURCE_FILES
	PBF/SimulationDataPBF.cpp
	PBF/TimeStepPBF.cpp
	PBF/TimeIntegration.cpp
	)	
	
set(IISPH_HEADER_FILES
	IISPH/SimulationDataIISPH.h
	IISPH/TimeStepIISPH.h
	)
	
set(IISPH_SOURCE_FILES
	IISPH/SimulationDataIISPH.cpp
	IISPH/TimeStepIISPH.cpp
	)		
	
set(DFSPH_HEADER_FILES
	DFSPH/SimulationDataDFSPH.h
	DFSPH/TimeStepDFSPH.h
	)
	
set(DFSPH_SOURCE_FILES
	DFSPH/SimulationDataDFSPH.cpp
	DFSPH/TimeStepDFSPH.cpp
	)	
	
set(SURFACETENSION_HEADER_FILES
	SurfaceTension/SurfaceTension_Becker2007.h
	SurfaceTension/SurfaceTension_Akinci2013.h
	SurfaceTension/SurfaceTension_He2014.h
	)
	
set(SURFACETENSION_SOURCE_FILES
	SurfaceTension/SurfaceTension_Becker2007.cpp
	SurfaceTension/SurfaceTension_Akinci2013.cpp
	SurfaceTension/SurfaceTension_He2014.cpp
	)	

set(VISCOSITY_HEADER_FILES
	Viscosity/Viscosity_XSPH.h
	Viscosity/Viscosity_Standard.h
	)
	
set(VISCOSITY_SOURCE_FILES
	Viscosity/Viscosity_XSPH.cpp
	Viscosity/Viscosity_Standard.cpp
	)	
	
set(UTILS_HEADER_FILES
	Utilities/PoissonDiskSampling.h
	Utilities/Timing.h
	)
	
set(UTILS_SOURCE_FILES
	Utilities/PoissonDiskSampling.cpp
	Utilities/Timing.cpp
	)	
	
find_package( Eigen3 REQUIRED )
include_directories( ${EIGEN3_INCLUDE_DIR} )

############################################################
# CompactNSearch
############################################################
include_directories(${PROJECT_PATH}/extern/install/CompactNSearch/include)

add_library(SPlisHSPlasH
	Common.h
	FluidModel.cpp
	FluidModel.h
	RigidBodyObject.h
	SPHKernels.cpp
	SPHKernels.h
	StaticRigidBody.h
	SurfaceTensionBase.cpp
	SurfaceTensionBase.h
	TimeManager.cpp
	TimeManager.h	
	TimeStep.cpp
	TimeStep.h
	TriangleMesh.cpp
	TriangleMesh.h
	ViscosityBase.cpp
	ViscosityBase.h
	
	${WCSPH_HEADER_FILES}
	${WCSPH_SOURCE_FILES}
	
	${PCISPH_HEADER_FILES}
	${PCISPH_SOURCE_FILES}
	
	${PBF_HEADER_FILES}
	${PBF_SOURCE_FILES}
	
	${IISPH_HEADER_FILES}
	${IISPH_SOURCE_FILES}
	
	${DFSPH_HEADER_FILES}
	${DFSPH_SOURCE_FILES}
	
	${VISCOSITY_HEADER_FILES}
	${VISCOSITY_SOURCE_FILES}
	
	${SURFACETENSION_HEADER_FILES}
	${SURFACETENSION_SOURCE_FILES}
	
	${UTILS_HEADER_FILES}
	${UTILS_SOURCE_FILES}
	
	CMakeLists.txt
)

add_dependencies(SPlisHSPlasH ExternalProject_CompactNSearch)

source_group("Header Files\\WCSPH" FILES ${WCSPH_HEADER_FILES})
source_group("Source Files\\WCSPH" FILES ${WCSPH_SOURCE_FILES})
source_group("Header Files\\PCISPH" FILES ${PCISPH_HEADER_FILES})
source_group("Source Files\\PCISPH" FILES ${PCISPH_SOURCE_FILES})
source_group("Header Files\\PBF" FILES ${PBF_HEADER_FILES})
source_group("Source Files\\PBF" FILES ${PBF_SOURCE_FILES})
source_group("Header Files\\IISPH" FILES ${IISPH_HEADER_FILES})
source_group("Source Files\\IISPH" FILES ${IISPH_SOURCE_FILES})
source_group("Header Files\\DFSPH" FILES ${DFSPH_HEADER_FILES})
source_group("Source Files\\DFSPH" FILES ${DFSPH_SOURCE_FILES})
source_group("Header Files\\Viscosity" FILES ${VISCOSITY_HEADER_FILES})
source_group("Source Files\\Viscosity" FILES ${VISCOSITY_SOURCE_FILES})
source_group("Header Files\\SurfaceTension" FILES ${SURFACETENSION_HEADER_FILES})
source_group("Source Files\\SurfaceTension" FILES ${SURFACETENSION_SOURCE_FILES})
source_group("Header Files\\Utils" FILES ${UTILS_HEADER_FILES})
source_group("Source Files\\Utils" FILES ${UTILS_SOURCE_FILES})

