SRCDIR = ../../source
SRCS = $(SRCDIR)/RenderingPlugin.cpp \
$(SRCDIR)/RenderAPI.cpp \
$(SRCDIR)/RenderAPI_OpenGLCoreES.cpp \
$(SRCDIR)/RenderAPI_Vulkan.cpp
OBJS = ${SRCS:.cpp=.o}
UNITY_DEFINES = -DSUPPORT_VULKAN=1 -DUNITY_LINUX=1
CXXFLAGS = $(UNITY_DEFINES) -O2 -fPIC
LDFLAGS = -shared -rdynamic
LIBS = -lGL
PLUGIN_SHARED = libRenderingPlugin.so
CXX ?= g++
PROJECT_PLUGIN_DIR = ../../../UnityProject/Assets/Plugins/RenderingPlugin

.cpp.o:
	$(CXX) $(CXXFLAGS) -c -o $@ $<

all: copy

clean:
	rm -f $(OBJS) $(PLUGIN_SHARED)

shared: $(OBJS)
	$(CXX) $(LDFLAGS) -o $(PLUGIN_SHARED) $(OBJS) $(LIBS)

copy: shared
	cp $(PLUGIN_SHARED) $(PROJECT_PLUGIN_DIR)
