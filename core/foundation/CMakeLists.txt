############################################################################
# CMakeLists.txt file for building ROOT core/foundation package
############################################################################

set(Foundation_dict_headers
  ESTLType.h
  RStringView.h
  TClassEdit.h
  ROOT/RIntegerSequence.hxx
  ROOT/RMakeUnique.hxx
  ROOT/RNotFn.hxx
  ROOT/RSpan.hxx
  ROOT/RStringView.hxx
  ROOT/span.hxx
  ROOT/TypeTraits.hxx
  PARENT_SCOPE
)

set(sources
  src/RConversionRuleParser.cxx
  src/TClassEdit.cxx
)

ROOT_OBJECT_LIBRARY(Foundation ${sources})
target_include_directories(Foundation PRIVATE res)

ROOT_OBJECT_LIBRARY(Foundation_Stage1 ${sources}) # used by rootcling_stage1
target_include_directories(Foundation_Stage1 PRIVATE res)
set_target_properties(Foundation_Stage1 PROPERTIES COMPILE_FLAGS "${COMPILE_FLAGS} ${CLING_CXXFLAGS}")

ROOT_INSTALL_HEADERS()
ROOT_ADD_TEST_SUBDIRECTORY(test)
