TARGET=libcspider.so
CC=gcc
CFLAGS=-ggdb -o3 -w -I includes -I /usr/include/libxml2 -I/usr/local/include -fpic -L/usr/local/lib
LIBFLAG=-luv -lcurl -lpcre -lxml2 -luri
C_SOURCES=$(shell find . -name "*.c")
C_OBJECTS=$(patsubst %.c, %.o, $(C_SOURCES))
HEADERS=$(shell find . -name "*.h")
TEMP=$(shell find . -name "*~")

$(TARGET): $(C_OBJECTS)
	$(CC) -shared -o $(TARGET) $(C_OBJECTS) $(LIBFLAG)
install:
	sudo cp $(TARGET) /usr/lib
	if [ ! -d "/usr/include/cspider" ]; then sudo mkdir /usr/include/cspider; fi;
	sudo cp $(HEADERS) /usr/include/cspider
uninstall:
	sudo rm -rf /usr/include/cspider
	sudo rm -f /usr/lib/libcspider.so

%.o: $(C_SOURCES) %.h
	$(CC) -c $(CFLAGS) $(LIBFLAG)$< -o $@
clean:
	rm -f $(shell find . -name "*.o") $(TEMP) $(TARGET)
