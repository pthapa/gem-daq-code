BUILD_HOME:=$(shell pwd)/../..

include $(XDAQ_ROOT)/config/mfAutoconf.rules
include $(XDAQ_ROOT)/config/mfDefs.$(XDAQ_OS)

# ROOT Config
ROOTCFLAGS   = $(shell root-config --cflags)
ROOTLIBS     = $(shell root-config --libs) 
ROOTGLIBS    = $(shell root-config --glibs) 

#Project=gem
Project=gemdaq-testing
Package=gemsupervisor
LongPackage=gemsupervisor
ShortPackage=supervisor
PackageName=supervisor

#Sources= GemSupervisorWeb.cc version.cc
#Sources= GEMTestBeamSupervisor.cc GEMTestBeamSupervisorWeb.cc
Sources= tbutils/VFAT2XMLParser.cc tbutils/GEMTBUtil.cc tbutils/ThresholdScan.cc tbutils/ADCScan.cc tbutils/LatencyScan.cc GEMGLIBSupervisorWeb.cc GEMDataParker.cc
#Sources= GEMGLIBSupervisorWeb.cc GEMDataParker.cc

DynamicLibrary=gem_supervisor

IncludeDirs = \
        $(BUILD_HOME)/$(Project)/$(Package)/include \
        $(BUILD_HOME)/$(Project)/gemhardware/include \
        $(XDAQ_ROOT)/include \
        $(uHALROOT)/include \
	$(ROOTDIR)/include 
#        $(BUILD_HOME)/gembase/include

DependentLibraryDirs = \
        $(XDAQ_ROOT)/lib \
        $(BUILD_HOME)/$(Project)/gemhardware/lib \
        $(uHALROOT)/lib 
#        /usr/include/root 
#        $(BUILD_HOME)/gembase/lib 

LibraryDirs = \
        $(XDAQ_ROOT)/lib \
        $(BUILD_HOME)/$(Project)/gemhardware/lib \
        $(uHALROOT)/lib \
        /usr/lib64/root 
#        $(BUILD_HOME)/gembase/lib 

PROFILING_Flags = -pg
DEBUG_CFlags  =  -O0 -g3 -fno-inline
DEBUG_CCFlags =  ${DEBUG_CFlags}
UserCFlags  = -std=c++0x ${ROOTCFLAGS} ${DEBUG_CFlags}
UserCCFlags = -std=c++0x ${ROOTCFLAGS} ${DEBUG_CCFlags}
UserDynamicLinkFlags = $(ROOTLIBS)
UserStaticLinkFlags =
#UserExecutableLinkFlags = -Wl,-rpath-link ${XDAQ_ROOT}/lib -Wl,-rpath-link $(uHALROOT)/lib -Wl,-rpath-link ${HCAL_XDAQ_ROOT}/lib \
#                          -L$(CACTUS_HOME)/lib \
#                          -lreadline -lncurses -lpthread -lboost_filesystem -lboost_regex -lboost_system -lcactus_extern_pugixml -lcactus_uhal_log -lcactus_uhal_grammars -lcactus_uhal_uhal
#LDFLAGS=`root-config --libs --glibs`
DEBUG_LIBS = profiler tcmalloc
DependentLibraries = config xcept boost_system cactus_uhal_uhal xerces-c
Libraries = config xcept numa toolbox asyncresolv uuid log4cplus xerces-c

include $(XDAQ_ROOT)/config/Makefile.rules
include $(XDAQ_ROOT)/config/mfRPM.rules

print-env:
	@echo BUILD_HOME $(BUILD_HOME)
	@echo XDAQ_ROOT  $(XDAQ_ROOT)
	@echo XDAQ_OS    $(XDAQ_OS)
	@echo ROOTCFLAGS $(ROOTCFLAGS)
	@echo ROOTLIBS   $(ROOTLIBS)
	@echo ROOTGLIBS  $(ROOTGLIBS)

