FLAGS= -g -shared -o
INCLUDE= -I$(CUBESYSPATH)/include/ -I$(CUBELIBPATH)/include -I$(CUBEAPPPATH)/include
CFLAGS= -g -c -fPIC -DUSER_MODE $(INCLUDE)
CC=gcc
CCP=g++
PLUGIN=vtcm_init
PLUGIN_OBJ=
INSTANCE_DIR= $(CUBEAPPPATH)/vtcm_emulator/
TEST_LIB= -L$(CUBELIBPATH)/lib -lsys_func -lexmodule -lmessage -lmemdb -lconnector -lstruct -lcrypto_func -ljson -lstring -lalloc -lpthread

main: lib$(PLUGIN).so
lib$(PLUGIN).so:  $(PLUGIN).o $(PLUGIN_PROC_OBJ) $(INIT_DB_OBJ)
	$(CC) $(FLAGS) lib$(PLUGIN).so $(PLUGIN).o $(PLUGIN_OBJ) $(TEST_LIB)
	cp lib$(PLUGIN).so $(CUBEAPPPATH)/vtcm_emulator
	cp lib$(PLUGIN).so $(CUBEAPPPATH)/vtcm_new_emulator
	mv lib$(PLUGIN).so $(INSTANCE_DIR)
	cp $(PLUGIN).cfg $(INSTANCE_DIR)
$(PLUGIN).o: $(PLUGIN).c $(PLUGIN).h
	$(CC) $(CFLAGS) $(PLUGIN).c
clean:
	rm -f test_main lib$(PLUGIN).so 
	rm  *.o *~
