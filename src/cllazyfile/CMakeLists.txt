
set( clLazyFile_SRCS
  lazyDataSectionReader.cc
  lazyFileReader.cc
  lazyInstMgr.cc
  p21HeaderSectionReader.cc
  sectionReader.cc
  lazyP21DataSectionReader.cc
  ../base/judy/src/judy.c
  ../base/judy/src/judyLArray.h
  ../base/judy/src/judySArray.h
  )

set( SC_CLLAZYFILE_HDRS
  headerSectionReader.h
  lazyFileReader.h
  lazyP21DataSectionReader.h
  p21HeaderSectionReader.h
  lazyDataSectionReader.h
  lazyInstMgr.h
  lazyTypes.h
  sectionReader.h
  instMgrHelper.h
  )

include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${SC_SOURCE_DIR}/src/cleditor
  ${SC_SOURCE_DIR}/src/cldai
  ${SC_SOURCE_DIR}/src/clstepcore
  ${SC_SOURCE_DIR}/src/clutils
  ${SC_SOURCE_DIR}/src/base
  ${SC_SOURCE_DIR}/src/base/judy/src
  )

SC_ADDLIB(steplazyfile "${clLazyFile_SRCS};${clLazyFile_HDRS}" "stepcore;stepdai;steputils;base")
SC_ADDEXEC(lazy_test "lazy_test.cc" "steplazyfile;stepeditor" )
set_target_properties(lazy_test PROPERTIES COMPILE_FLAGS "-DNO_REGISTRY" )

install(FILES ${SC_CLLAZYFILE_HDRS}
  DESTINATION ${INCLUDE_INSTALL_DIR}/stepcode/cllazyfile)

# Local Variables:
# tab-width: 8
# mode: cmake
# indent-tabs-mode: t
# End:
# ex: shiftwidth=2 tabstop=8

