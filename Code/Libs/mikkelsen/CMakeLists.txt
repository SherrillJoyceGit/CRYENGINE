#START-FILE-LIST
# File List auto generated by waf2cmake.py, do not modify manually.

start_sources()
# -- mikkelsen.waf_files --
sources_platform(ALL)
add_sources("NoUberFile"
	SOURCE_GROUP "Root"
		"${SDK_DIR}/TangentBasisComputation/mikkelsen/mikktspace.cpp"
		"${SDK_DIR}/TangentBasisComputation/mikkelsen/mikktspace.h"
)

end_sources()
#END-FILE-LIST

if (WINDOWS)
	set(DISABLE_WARNINGS /W0)  # Disable warnings from 3rdParty code.
else()
	set(DISABLE_WARNINGS -w)
endif()

CryEngineStaticModule(mikkelsen SOLUTION_FOLDER "Libs")
target_include_directories(${THIS_PROJECT} PRIVATE "${SDK_DIR}/TangentBasisComputation/mikkelsen")
target_compile_options(${THIS_PROJECT} PRIVATE ${DISABLE_WARNINGS})
target_compile_definitions(${THIS_PROJECT} PRIVATE -DHDF) # Because we want to support HDF in this library
target_include_directories(${THIS_PROJECT} INTERFACE "${SDK_DIR}/TangentBasisComputation")
