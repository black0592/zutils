CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
PROJECT (c1000k)

IF(CMAKE_SYSTEM MATCHES Linux)
  ADD_DEFINITIONS(-D__LINUX__)
  ADD_DEFINITIONS(-D__linux)
  ADD_DEFINITIONS(-D_REENTRANT)
ENDIF(CMAKE_SYSTEM MATCHES Linux)

INCLUDE_DIRECTORIES(${PROJECT_SOURCE_DIR})
INCLUDE_DIRECTORIES(../)

SET(EXECUTABLE_OUTPUT_PATH ${TF_CURRENT_BINARY_PATH_BIN})

LINK_DIRECTORIES(${TF_CURRENT_BINARY_PATH_LIB})

SET (C1000K_LIST 
		./c1000k.cc
	)
	
ADD_EXECUTABLE(c1000k ${C1000K_LIST})
	
SET (C1000K_CLIENT_LIST 
		./c1000k_client.cc
	)

ADD_EXECUTABLE(c1000k_client ${C1000K_CLIENT_LIST})

##update_end
TARGET_LINK_LIBRARIES(c1000k net base2 base libevent pthread rt)
TARGET_LINK_LIBRARIES(c1000k_client net base2 base libevent pthread rt)

