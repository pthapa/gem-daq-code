BUILD_HOME:=$(shell pwd)/../..

include $(XDAQ_ROOT)/config/mfAutoconf.rules
include $(XDAQ_ROOT)/config/mfDefs.$(XDAQ_OS)

#Project=gem
Project=gemdaq-testing
Package=gemhardware
LongPackage=gemhardware
ShortPackage=hw
PackageName=hw

Sources= GEMHwDevice.cc \
	HwVFAT2.cc  VFAT2Manager.cc VFAT2ControlPanelWeb.cc \
	HwOptoHybrid.cc \
	HwGLIB.cc \
	GEMController.cc GEMControllerPanelWeb.cc
##version.cc

DynamicLibrary=gem_hw

IncludeDirs = \
        $(BUILD_HOME)/$(Project)/$(Package)/include \
        $(XDAQ_ROOT)/include \
        $(uHALROOT)/include
#        $(BUILD_HOME)/$(Project)/gembase/include \

DependentLibraryDirs = \
        $(XDAQ_ROOT)/lib \
        $(uHALROOT)/lib

LibraryDirs = \
        $(XDAQ_ROOT)/lib \
        $(uHALROOT)/lib

PROFILING_Flags = -pg
DEBUG_CFlags  =  -O0 -g3 -fno-inline
DEBUG_CCFlags =  ${DEBUG_CFlags}
UserCFlags  = -std=c++0x ${DEBUG_CFlags}
UserCCFlags = -std=c++0x ${DEBUG_CCFlags}
DEBUG_LDFlags = ${PROFILING_Flags}
UserDynamicLinkFlags = 
UserStaticLinkFlags =
#UserExecutableLinkFlags = -Wl,-rpath-link ${XDAQ_ROOT}/lib -Wl,-rpath-link $(uHALROOT)/lib -Wl,-rpath-link ${HCAL_XDAQ_ROOT}/lib \
#                          -L$(CACTUS_HOME)/lib \
#                          -lreadline -lncurses -lpthread -lboost_filesystem -lboost_regex -lboost_system -lcactus_extern_pugixml -lcactus_uhal_log -lcactus_uhal_grammars -lcactus_uhal_uhal

DEBUG_LIBS = profiler tcmalloc
DependentLibraries = config xcept boost_system cactus_uhal_uhal
Libraries = config xcept numa toolbox xdaq2rc asyncresolv uuid log4cplus cactus_uhal_uhal

include $(XDAQ_ROOT)/config/Makefile.rules
include $(XDAQ_ROOT)/config/mfRPM.rules
