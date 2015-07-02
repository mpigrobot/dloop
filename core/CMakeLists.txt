SET(CORE_DIRS
	${CMAKE_SOURCE_DIR}/core/DBoW2
	${CMAKE_SOURCE_DIR}/core/DUtils
	${CMAKE_SOURCE_DIR}/core/DVision
	${CMAKE_SOURCE_DIR}/core/DLoopDetector
	${CMAKE_SOURCE_DIR}/core/DUtilsCV
 CACHE INTERNAL "include directories")

SET(LIB_CPP_LIST ${})

FOREACH(dir ${CORE_DIRS})
	aux_source_directory(${dir} CPPS)
	
	if(dir STREQUAL "DLoopDetector")
		file(GLOB CPPS RELATIVE "${dir}" "*.h")	
	endif()	
	
	list(APPEND LIB_CPP_LIST ${LIB_CPP_LIST} ${CPPS})
	#message(STATUS "${dir} contains ${CPPS}")
ENDFOREACH(dir ${CORE_DIRS})

#find_package(OpenCV REQUIRED)
include_directories(${CORE_DIRS})

add_library(dloop SHARED ${LIB_CPP_LIST})
target_link_libraries(dloop ${OpenCV_LIBS})
#message(STATUS "OpenCV_INCLUDE_DIRS = ${OpenCV_INCLUDE_DIRS}")
#message(STATUS "OpenCV_LIB_DIRS = ${OpenCV_LIB_DIRS}")
#message(STATUS "OpenCV_LIBRARIES = ${OpenCV_LIBRARIES}")
#message(STATUS "OpenCV_LIBS = ${OpenCV_LIBS}")
#message(STATUS "OpenCV_VERSION = ${OpenCV_VERSION}")



