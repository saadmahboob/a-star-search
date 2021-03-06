CC = gcc
CFLAGS = -g -std=c99 -Wall
SLIBS = -lcheck
SRC = ../src
OBJECTS = check_linkedlist.o check_arraylist.o check_listqueue.o check_liststack.o check_arrayheap.o check_heappriorityqueue.o check_treemap.o check_treeset.o check_hashmap.o check_hashset.o
INCLUDES = list.h linkedlist.h arraylist.h queue.h listqueue.h stack.h liststack.h heap.h arrayheap.h priorityqueue.h heappriorityqueue.h set.h treeset.h hashset.h map.h treemap.h hashmap.h hashset.h
TESTS = check_linkedlist check_arraylist check_listqueue check_liststack check_arrayheap check_heappriorityqueue check_treemap check_treeset check_hashmap check_hashset

ifndef V
        QUIET_CC        = @echo '   ' CC $@;
        QUIET_AR        = @echo '   ' AR $@;
        QUIET_LINK      = @echo '   ' LINK $@;
        QUIET_GEN       = @echo '   ' GEN $@;
        QUIET_RM        = @echo '   ' RM  $@;
        QUIET_OBJCPY    = @echo '   ' OBJCPY $@;
endif

LIBINCLUDES = $(INCLUDES:%=$(SRC)/%)

all: $(TESTS)

%.o : %.c $(SRC)/$(LIBINCLUDES)
	$(QUIET_CC) $(CC) $(CFLAGS) -c -o $@ $<

check_linkedlist: check_linkedlist.o $(SRC)/linkedlist.o 
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_arraylist: check_arraylist.o $(SRC)/arraylist.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_listqueue: check_listqueue.o $(SRC)/linkedlist.o $(SRC)/listqueue.o 
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_liststack: check_liststack.o $(SRC)/linkedlist.o $(SRC)/liststack.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_arrayheap: check_arrayheap.o $(SRC)/arraylist.o $(SRC)/arrayheap.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_heappriorityqueue: check_heappriorityqueue.o $(SRC)/arraylist.o $(SRC)/arrayheap.o $(SRC)/heappriorityqueue.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_treemap: check_treemap.o $(SRC)/treemap.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_treeset: check_treeset.o $(SRC)/treeset.o $(SRC)/treemap.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_hashmap: check_hashmap.o $(SRC)/hashmap.o $(SRC)/arraylist.o $(SRC)/linkedlist.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check_hashset: check_hashset.o $(SRC)/hashset.o $(SRC)/hashmap.o $(SRC)/arraylist.o $(SRC)/linkedlist.o
	$(QUIET_GEN) $(CC) $(CFLAGS) -o $@ $^ $(SLIBS)

check: $(TESTS)
	for t in $(TESTS); \
	do \
		echo " "; \
		./$$t; \
	done

clean:
	rm -f $(TESTS) $(OBJECTS)

help:
	@echo "make" or "make all" to build tests
	@echo "make check" to run tests