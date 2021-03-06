#include ../Makefile.inc
#PIN_ROOT=$(PIN_PATH)
CONFIG_ROOT=$(PIN_ROOT)/source/tools/Config
include $(CONFIG_ROOT)/makefile.config

TEST_TOOL_ROOTS =  cct_client deadspy_client redspy_client redspy_temporal_client redspy_temporal_approx_client cct_data_centric_client cct_client_mem_only cct_data_centric_client_tree_based redspy_spatial_client redspy_spatial_approx_client cct_metric_client cctlib_reader footprint_client footprint_client2 valueNum omp_datarace_client cache
APP_ROOTS = deadWrites threaded 
#all:  cct_client.so  deadspy_client.so cct_data_centric_client.so cct_client_mem_only.so cct_data_centric_client_tree_based.so deadWrites 

ALLOW_UNUSED_BUT_SET= -Wno-unused-but-set-variable
CCTLIB_TEST_FLAGS =  $(CCTLIB_EXTRA_CXXFLAGS)  $(CCTLIB_EXTRA_CPPFLAGS) $(TOOL_CXXFLAGS) -I$(SPARSEHASH_PATH)/include -I../src/ $(ALLOW_UNUSED_BUT_SET)

if OPT_USE_BOOST
	CCTLIB_TEST_FLAGS +=  -I$(BOOST_PATH)/include 
	BOOST_LD_FLAGS =  -L$(BOOST_PATH)/lib -Wl,-rpath $(BOOST_PATH)/lib 
	BOOST_LIBS =  -lboost_filesystem 
endif

LIBELF_LD_FLAGS= -L$(LIBELF_PATH)/lib -Wl,-rpath $(LIBELF_PATH)/lib
LIBELF_LIBS = -lelf
CLIENT_LD_FLAGS = $(BOOST_LD_FLAGS) $(LIBELF_LD_FLAGS)
CLIENT_LIBS = $(BOOST_LIBS) $(LIBELF_LIBS)


CCTLIB_SHADOW_BASED_LIBRARY=../src/$(OBJDIR)libcctlib$(LIB_SUFFIX)
CCTLIB_TREE_BASED_LIBRARY=../src/$(OBJDIR)libcctlib_tree_based$(LIB_SUFFIX)

$(OBJDIR)cct_client$(OBJ_SUFFIX): cct_client.cpp ../src/cctlib.H
	$(CXX) $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)cct_client$(PINTOOL_SUFFIX): $(OBJDIR)cct_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)deadspy_client$(OBJ_SUFFIX): deadspy_client.cpp ../src/cctlib.H
	$(CXX) -Wno-deprecated  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)deadspy_client$(PINTOOL_SUFFIX): $(OBJDIR)deadspy_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)redspy_client$(OBJ_SUFFIX): redspy_client.cpp ../src/cctlib.H
	$(CXX) -Wno-deprecated  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)redspy_client$(PINTOOL_SUFFIX): $(OBJDIR)redspy_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)redspy_temporal_client$(OBJ_SUFFIX): redspy_temporal_client.cpp ../src/cctlib.H
	$(CXX) -Wno-deprecated  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)redspy_temporal_client$(PINTOOL_SUFFIX): $(OBJDIR)redspy_temporal_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)redspy_temporal_approx_client$(OBJ_SUFFIX): redspy_temporal_approx_client.cpp ../src/cctlib.H
	$(CXX) -Wno-deprecated  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)redspy_temporal_approx_client$(PINTOOL_SUFFIX): $(OBJDIR)redspy_temporal_approx_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)


$(OBJDIR)omp_datarace_client$(OBJ_SUFFIX): omp_datarace_client.cpp ../src/cctlib.H shadow_memory.cpp
	$(CXX) -Wno-deprecated  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)omp_datarace_client$(PINTOOL_SUFFIX): $(OBJDIR)omp_datarace_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)


$(OBJDIR)cct_data_centric_client$(OBJ_SUFFIX): cct_data_centric_client.cpp ../src/cctlib.H
	$(CXX) $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)cct_data_centric_client$(PINTOOL_SUFFIX): $(OBJDIR)cct_data_centric_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)


$(OBJDIR)cct_client_mem_only$(OBJ_SUFFIX): cct_client_mem_only.cpp ../src/cctlib.H
	$(CXX) $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)cct_client_mem_only$(PINTOOL_SUFFIX): $(OBJDIR)cct_client_mem_only$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)


$(OBJDIR)cctlib_reader$(OBJ_SUFFIX): cctlib_reader.cpp ../src/cctlib.H
	$(CXX) $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)cctlib_reader$(PINTOOL_SUFFIX): $(OBJDIR)cctlib_reader$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)


$(OBJDIR)cct_data_centric_client_tree_based$(OBJ_SUFFIX): cct_data_centric_client_tree_based.cpp ../src/cctlib.H
	$(CXX) $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)cct_data_centric_client_tree_based$(PINTOOL_SUFFIX): $(OBJDIR)cct_data_centric_client_tree_based$(OBJ_SUFFIX) $(CCTLIB_TREE_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS) -lcctlib_tree_based  $(TOOL_LIBS) $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)redspy_spatial_client$(OBJ_SUFFIX): redspy_spatial_client.cpp ../src/cctlib.H
	$(CXX)  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)redspy_spatial_client$(PINTOOL_SUFFIX): $(OBJDIR)redspy_spatial_client$(OBJ_SUFFIX) $(CCTLIB_TREE_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib_tree_with_addr  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)redspy_spatial_approx_client$(OBJ_SUFFIX): redspy_spatial_approx_client.cpp ../src/cctlib.H
	$(CXX)  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)redspy_spatial_approx_client$(PINTOOL_SUFFIX): $(OBJDIR)redspy_spatial_approx_client$(OBJ_SUFFIX) $(CCTLIB_TREE_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib_tree_with_addr  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)


$(OBJDIR)cct_metric_client$(OBJ_SUFFIX): cct_metric_client.cpp ../src/cctlib.H
	$(CXX)  $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)cct_metric_client$(PINTOOL_SUFFIX): $(OBJDIR)cct_metric_client$(OBJ_SUFFIX) $(CCTLIB_TREE_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib_metric  $(TOOL_LIBS)   $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

#Value numbering 
$(OBJDIR)valueNum$(OBJ_SUFFIX): valueNum.cpp ../src/cctlib.H
	$(CXX) $(CCTLIB_TEST_FLAGS)  $(COMP_OBJ)$@ $<

$(OBJDIR)valueNum$(PINTOOL_SUFFIX): $(OBJDIR)valueNum$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib  $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)


#Footprint clients
$(OBJDIR)footprint_client$(OBJ_SUFFIX): footprint_client.cpp ../src/cctlib.H ../src/cctlib.cpp
	$(CXX) $(CCTLIB_TEST_FLAGS) -DHAVE_METRIC_PER_IPNODE $(COMP_OBJ)$@ $<

$(OBJDIR)footprint_client$(PINTOOL_SUFFIX): $(OBJDIR)footprint_client$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_PER_IPNODE_METRIC_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib_metric  $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)footprint_client2$(OBJ_SUFFIX): footprint_client2.cpp ../src/cctlib.H ../src/cctlib.cpp
	$(CXX) $(CCTLIB_TEST_FLAGS) -DHAVE_METRIC_PER_IPNODE $(COMP_OBJ)$@ $<

$(OBJDIR)footprint_client2$(PINTOOL_SUFFIX): $(OBJDIR)footprint_client2$(OBJ_SUFFIX) $(CCTLIB_SHADOW_BASED_PER_IPNODE_METRIC_LIBRARY)
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)  -lcctlib_metric  $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)

$(OBJDIR)cache$(OBJ_SUFFIX): cache.cpp 
	$(CXX) $(CCTLIB_TEST_FLAGS) $(COMP_OBJ)$@ $<

$(OBJDIR)cache$(PINTOOL_SUFFIX): $(OBJDIR)cache$(OBJ_SUFFIX) 
	$(LINKER) $(TOOL_LDFLAGS) $(LINK_EXE)$@ $< -L../src/$(OBJDIR) $(TOOL_LPATHS)   $(TOOL_LIBS)  $(CLIENT_LD_FLAGS) $(CLIENT_LIBS)



include $(TOOLS_ROOT)/Config/makefile.default.rules

clean-local:
	rm -f $(OBJDIR)/*

