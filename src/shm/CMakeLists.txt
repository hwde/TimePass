INCLUDE_DIRECTORIES(include ${GLOBAL_BASE}/include)
LINK_DIRECTORIES (${LIBRARY_OUTPUT_PATH})

AUX_SOURCE_DIRECTORY(${SHM_BASE}/src SHM_SRC)

FILE(GLOB SHM_INCLUDE ${SHM_BASE}/include/*)

ADD_LIBRARY(libshm SHARED ${SHM_SRC})
ADD_LIBRARY(shm_static STATIC ${SHM_SRC})

TARGET_LINK_LIBRARIES(libshm libglobal)

MESSAGE("DEBUG MSG:")
MESSAGE(${CMAKE_INSTALL_PREFIX}/include/timepass)

INSTALL(TARGETS libshm LIBRARY DESTINATION  lib)
INSTALL(TARGETS shm_static ARCHIVE DESTINATION  lib)
INSTALL(FILES  ${SHM_INCLUDE} DESTINATION  include/shm)

SET_TARGET_PROPERTIES(libshm PROPERTIES OUTPUT_NAME "shm")
SET_TARGET_PROPERTIES(shm_static PROPERTIES OUTPUT_NAME "shm")