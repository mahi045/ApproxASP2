set(header_path ${CLINGO_SOURCE_DIR}/libgringo)
# [[[header: .
set(ide_header_group "Header Files")
set(header-group
    "${header_path}/clingo.h")
source_group("${ide_header_group}" FILES ${header-group})
set(header-group-gringo
    "${header_path}/gringo/utility.hh"
    "${header_path}/gringo/scripts.hh"
    "${header_path}/gringo/safetycheck.hh"
    "${header_path}/gringo/domain.hh"
    "${header_path}/gringo/lua.hh"
    "${header_path}/gringo/python.hh"
    "${header_path}/gringo/control.hh"
    "${header_path}/gringo/clonable.hh"
    "${header_path}/gringo/indexed.hh"
    "${header_path}/gringo/symbol.hh"
    "${header_path}/gringo/primes.hh"
    "${header_path}/gringo/lexerstate.hh"
    "${header_path}/gringo/bug.hh"
    "${header_path}/gringo/hash_set.hh"
    "${header_path}/gringo/backtrace.hh"
    "${header_path}/gringo/logger.hh"
    "${header_path}/gringo/base.hh"
    "${header_path}/gringo/printable.hh"
    "${header_path}/gringo/hashable.hh"
    "${header_path}/gringo/types.hh"
    "${header_path}/gringo/locatable.hh"
    "${header_path}/gringo/term.hh"
    "${header_path}/gringo/graph.hh"
    "${header_path}/gringo/intervals.hh"
    "${header_path}/gringo/backend.hh"
    "${header_path}/gringo/comparable.hh"
    "${header_path}/gringo/terms.hh")
source_group("${ide_header_group}\\gringo" FILES ${header-group-gringo})
set(header-group-gringo-ground
    "${header_path}/gringo/ground/instantiation.hh"
    "${header_path}/gringo/ground/program.hh"
    "${header_path}/gringo/ground/literal.hh"
    "${header_path}/gringo/ground/dependency.hh"
    "${header_path}/gringo/ground/statements.hh"
    "${header_path}/gringo/ground/binders.hh"
    "${header_path}/gringo/ground/types.hh"
    "${header_path}/gringo/ground/statement.hh"
    "${header_path}/gringo/ground/literals.hh")
source_group("${ide_header_group}\\gringo\\ground" FILES ${header-group-gringo-ground})
set(header-group-gringo-input
    "${header_path}/gringo/input/program.hh"
    "${header_path}/gringo/input/programbuilder.hh"
    "${header_path}/gringo/input/groundtermparser.hh"
    "${header_path}/gringo/input/literal.hh"
    "${header_path}/gringo/input/theory.hh"
    "${header_path}/gringo/input/aggregate.hh"
    "${header_path}/gringo/input/aggregates.hh"
    "${header_path}/gringo/input/types.hh"
    "${header_path}/gringo/input/statement.hh"
    "${header_path}/gringo/input/nongroundparser.hh"
    "${header_path}/gringo/input/literals.hh")
source_group("${ide_header_group}\\gringo\\input" FILES ${header-group-gringo-input})
set(header-group-gringo-output
    "${header_path}/gringo/output/backends.hh"
    "${header_path}/gringo/output/literal.hh"
    "${header_path}/gringo/output/theory.hh"
    "${header_path}/gringo/output/aggregates.hh"
    "${header_path}/gringo/output/output.hh"
    "${header_path}/gringo/output/statements.hh"
    "${header_path}/gringo/output/types.hh"
    "${header_path}/gringo/output/statement.hh"
    "${header_path}/gringo/output/literals.hh")
source_group("${ide_header_group}\\gringo\\output" FILES ${header-group-gringo-output})
set(header
    ${header-group}
    ${header-group-gringo}
    ${header-group-gringo-ground}
    ${header-group-gringo-input}
    ${header-group-gringo-output})
# ]]]

set(source_path ${CLINGO_SOURCE_DIR}/libgringo)
# [[[source: ./src
set(ide_source_group "Source Files")
set(source-group
    "${source_path}/src/python.cc"
    "${source_path}/src/primes.cc"
    "${source_path}/src/lua.cc"
    "${source_path}/src/symbol.cc"
    "${source_path}/src/terms.cc"
    "${source_path}/src/backend.cc"
    "${source_path}/src/control.cc"
    "${source_path}/src/term.cc"
    "${source_path}/src/scripts.cc")
source_group("${ide_source_group}" FILES ${source-group})
set(source-group-ground
    "${source_path}/src/ground/instantiation.cc"
    "${source_path}/src/ground/program.cc"
    "${source_path}/src/ground/statements.cc"
    "${source_path}/src/ground/literals.cc")
source_group("${ide_source_group}\\ground" FILES ${source-group-ground})
set(source-group-input
    "${source_path}/src/input/groundtermparser.cc"
    "${source_path}/src/input/program.cc"
    "${source_path}/src/input/aggregate.cc"
    "${source_path}/src/input/aggregates.cc"
    "${source_path}/src/input/theory.cc"
    "${source_path}/src/input/programbuilder.cc"
    "${source_path}/src/input/literal.cc"
    "${source_path}/src/input/literals.cc"
    "${source_path}/src/input/statement.cc"
    "${source_path}/src/input/nongroundparser.cc")
source_group("${ide_source_group}\\input" FILES ${source-group-input})
set(source-group-output
    "${source_path}/src/output/aggregates.cc"
    "${source_path}/src/output/theory.cc"
    "${source_path}/src/output/statements.cc"
    "${source_path}/src/output/output.cc"
    "${source_path}/src/output/literal.cc"
    "${source_path}/src/output/literals.cc"
    "${source_path}/src/output/statement.cc")
source_group("${ide_source_group}\\output" FILES ${source-group-output})
set(source
    ${source-group}
    ${source-group-ground}
    ${source-group-input}
    ${source-group-output})
# ]]]

# TODO: complex enough to justify adding a function...
file(MAKE_DIRECTORY "${CMAKE_BINARY_DIR}/generated/libgringo/input/groundtermgrammar")
file(MAKE_DIRECTORY "${CMAKE_BINARY_DIR}/generated/libgringo/input/nongroundgrammar")
bison_target("groundtermgrammar" "${source_path}/src/input/groundtermgrammar.yy" "${CMAKE_BINARY_DIR}/generated/libgringo/input/groundtermgrammar/grammar.cc")
source_group("${ide_source_group}\\input" FILES "${source_path}/src/input/groundtermgrammar.yy")
bison_target("nongroundgrammar" "${source_path}/src/input/nongroundgrammar.yy" "${CMAKE_BINARY_DIR}/generated/libgringo/input/nongroundgrammar/grammar.cc")
source_group("${ide_source_group}\\input" FILES "${source_path}/src/input/nongroundgrammar.yy")
re2c_target(NAME "groundtermlexer" INPUT "${source_path}/src/input/groundtermlexer.xh" OUTPUT "${CMAKE_BINARY_DIR}/generated/libgringo/input/groundtermlexer.hh")
source_group("${ide_source_group}\\input" FILES "${source_path}/src/input/groundtermlexer.xh")
set_target_properties(groundtermlexer PROPERTIES FOLDER gen) # TODO: try to get rid of these as with the bison_target
re2c_target(NAME "nongroundlexer" INPUT "${source_path}/src/input/nongroundlexer.xch" OUTPUT "${CMAKE_BINARY_DIR}/generated/libgringo/input/nongroundlexer.hh" OPTIONS "-c")
source_group("${ide_source_group}\\input" FILES "${source_path}/src/input/nongroundlexer.xch")
set_target_properties(nongroundlexer PROPERTIES FOLDER gen) # TODO: try to get rid of these as with the bison_target

source_group("${ide_source_group}\\input\\nongroundgrammar" FILES 
    "${BISON_nongroundgrammar_OUTPUT_HEADER}"
    "${BISON_nongroundgrammar_OUTPUT_SOURCE}")
source_group("${ide_source_group}\\input\\groundtermgrammar" FILES 
    "${BISON_groundtermgrammar_OUTPUT_HEADER}"
    "${BISON_groundtermgrammar_OUTPUT_SOURCE}")
source_group("${ide_source_group}\\input" FILES 
    "${CMAKE_BINARY_DIR}/generated/libgringo/input/groundtermlexer.hh")
source_group("${ide_source_group}\\input" FILES 
    "${CMAKE_BINARY_DIR}/generated/libgringo/input/nongroundlexer.hh")

list(APPEND header
    "${BISON_nongroundgrammar_OUTPUT_HEADER}"
    "${BISON_groundtermgrammar_OUTPUT_HEADER}"
    "${CMAKE_BINARY_DIR}/generated/libgringo/input/groundtermlexer.hh"
    "${CMAKE_BINARY_DIR}/generated/libgringo/input/nongroundlexer.hh")
list(APPEND source
    "${source_path}/src/input/groundtermgrammar.yy"
    "${source_path}/src/input/nongroundgrammar.yy"
    "${source_path}/src/input/groundtermlexer.xh"
    "${source_path}/src/input/nongroundlexer.xch"
    "${BISON_nongroundgrammar_OUTPUT_SOURCE}"
    "${BISON_groundtermgrammar_OUTPUT_SOURCE}")

add_library(libgringo ${header} ${source})
target_include_directories(libgringo PUBLIC
    "$<BUILD_INTERFACE:${header_path}>"
    "$<BUILD_INTERFACE:${CMAKE_BINARY_DIR}/generated/libgringo>")
target_link_libraries(libgringo PUBLIC libpotassco libreify)
target_compile_definitions(libgringo PRIVATE
    CLINGO_BUILD_LIBRARY
    CLINGO_GRINGO_ONLY)
set_target_properties(libgringo PROPERTIES 
    OUTPUT_NAME gringo
    FOLDER lib)

if (CLINGO_ENABLE_LUA) 
    target_compile_definitions(libgringo PRIVATE WITH_LUA)
    target_link_libraries(libgringo PRIVATE ${LUA_LIBRARIES})
    target_include_directories(libgringo PRIVATE ${LUA_INCLUDE_DIR})
endif()
if (CLINGO_ENABLE_PYTHON) 
    target_compile_definitions(libgringo PRIVATE WITH_PYTHON)
    target_link_libraries(libgringo PRIVATE ${PYTHON_LIBRARIES})
    target_include_directories(libgringo PRIVATE ${PYTHON_INCLUDE_DIRS})
endif()

add_subdirectory(tests)
