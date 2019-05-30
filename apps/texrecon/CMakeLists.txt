file (GLOB HEADERS "*.h")
file (GLOB SOURCES "[^_]*.cpp")

set(BIN texrecon)

add_executable(${BIN} ${SOURCES})
set_property(TARGET ${BIN} PROPERTY INTERPROCEDURAL_OPTIMIZATION True)
#add_dependencies(${BIN} ext_mve)

message( WARNING "TBB_LIBRARIES = ${TBB_LIBRARIES}" )
target_link_libraries(${BIN}
	tex
	${TBB_LIBRARIES}
	-lmve
	-lmve_util
	#/home/vm/experimental/mve/rpici/mve/libs/mve/libmve.a
	#/home/vm/experimental/mve/rpici/mve/libs/util/libmve_util.a
)
install(TARGETS ${BIN} RUNTIME DESTINATION bin)
message( WARNING "End of texrecon CMakeLists.txt file" )
