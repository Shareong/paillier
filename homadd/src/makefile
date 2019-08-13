LIB_NAME ?= paillier

BUILD_PATH := ../build

MKDIR := mkdir 

#$(BUILD_PATH):
#	mkdir -p $(BUILD_PATH)

STATIC_NAME ?= lib$(LIB_NAME).a
SHARE_NAME  ?= lib$(LIB_NAME).so

TARGET_PATH := ../lib

#$(TARGET_PATH):
#	mkdir -p $(TARGET_PATH)

STATIC_TARGET := $(TARGET_PATH)/$(STATIC_NAME)
SHARE_TARGET := $(TARGET_PATH)/$(SHARE_NAME)

SOURCE :=$(wildcard *.c)
OBJS := $(patsubst %.c, $(BUILD_PATH)/%.o, $(wildcard *.c))

all: dir $(STATIC_TARGET) $(SHARE_TARGET)

dir:
	${MKDIR} -p $(BUILD_PATH)
	${MKDIR} -p $(TARGET_PATH) 

#generate libpaillier.a
$(STATIC_TARGET):$(OBJS) 
	ar cru $(STATIC_TARGET) $(OBJS) 
	ranlib $(STATIC_TARGET)

#generate libppaillier.so
$(SHARE_TARGET):$(OBJS)
	gcc -shared -fPIC -o $(SHARE_TARGET) $(SOURCE)

#generate binary file (*.o)
$(OBJS): $(wildcard *.c)
	gcc -c $< -o $@


clean:
	rm -rf $(BUILD_PATH)/*.o $(TARGET_PATH)/*.{a,so}

.PHONY: all clean
