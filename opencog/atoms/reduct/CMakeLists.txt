
# The atom_types.h file is written to the build directory
INCLUDE_DIRECTORIES( ${CMAKE_CURRENT_BINARY_DIR})

ADD_LIBRARY (clearbox SHARED
	FoldLink.cc
	FreeLink.cc
	PlusLink.cc
	TimesLink.cc
)

# Without this, parallel make will race and crap up the generated files.
ADD_DEPENDENCIES(clearbox opencog_atom_types)

TARGET_LINK_LIBRARIES(clearbox
	cogutil
)

INSTALL (FILES
	FoldLink.h
	FreeLink.h
	PlusLink.h
	TimesLink.h
	DESTINATION "include/${PROJECT_NAME}/atomspace"
)
