TARGET := main
CC := gcc
SRCEXT := c

TARGETDIR := bin
BUILDDIR := build
SRCDIR := src

CFLAGS := -Wall
INC := -I include

SOURCES := $(shell find $(SRCDIR) -name '*.$(SRCEXT)')
OBJECTS := $(patsubst $(SRCDIR)/%, $(BUILDDIR)/%, $(SOURCES:%.$(SRCEXT)=%.o))

.PHONY: all
all: $(TARGET)
	@echo "DONE"

-include $(OBJECTS:.o=.d)

$(TARGET): $(OBJECTS)
	$(CC) $(CFLAGS) $(INC) $(OBJECTS) -o $(TARGETDIR)/$(TARGET)

$(BUILDDIR)/%.o: $(SRCDIR)/%.$(SRCEXT)
	@mkdir -p `dirname $(BUILDDIR)/$*`
	$(CC) -c $(CFLAGS) $(INC) $< -o $@
	$(CC) -MM $(CFLAGS) $(INC) $< > $(BUILDDIR)/$*.d
	@mv -f $(BUILDDIR)/$*.d $(BUILDDIR)/$*.d.tmp
	@sed 's|.*:|$(BUILDDIR)/$*.o:|' < $(BUILDDIR)/$*.d.tmp > $(BUILDDIR)/$*.d
	@rm -f $(BUILDDIR)/$*.d.tmp

.PHONY: clean
clean:
	rm $(TARGETDIR)/$(TARGET)
	rm -rf build
	mkdir build