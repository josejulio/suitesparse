#-----------------------------------------------------------------------------
# compile the CAMD demo (for both GNU make or original make)
#-----------------------------------------------------------------------------

default: camd_simple camd_demo camd_demo2 camd_l_demo

include ../../SuiteSparse_config/SuiteSparse_config.mk

C = $(CC) $(CF) -I../Include -I../../SuiteSparse_config

INC = ../Include/camd.h ../../SuiteSparse_config/SuiteSparse_config.h

LIB2 = ../../SuiteSparse_config/libsuitesparseconfig.a $(LIB)

library:
	( cd ../../SuiteSparse_config ; $(MAKE) )
	( cd ../Lib ; $(MAKE) )

#------------------------------------------------------------------------------
# Create the demo program, run it, and compare the output
#------------------------------------------------------------------------------

dist:

camd_demo: camd_demo.c library $(INC)
	$(C) -o camd_demo camd_demo.c ../Lib/libcamd.a $(LIB2)
	./camd_demo > my_camd_demo.out
	- diff camd_demo.out my_camd_demo.out

camd_l_demo: camd_l_demo.c library $(INC)
	$(C) -o camd_l_demo camd_l_demo.c ../Lib/libcamd.a $(LIB2)
	./camd_l_demo > my_camd_l_demo.out
	- diff camd_l_demo.out my_camd_l_demo.out

camd_demo2: camd_demo2.c library $(INC)
	$(C) -o camd_demo2 camd_demo2.c ../Lib/libcamd.a $(LIB2)
	./camd_demo2 > my_camd_demo2.out
	- diff camd_demo2.out my_camd_demo2.out

camd_simple: camd_simple.c library $(INC)
	$(C) -o camd_simple camd_simple.c ../Lib/libcamd.a $(LIB2)
	./camd_simple > my_camd_simple.out
	- diff camd_simple.out my_camd_simple.out

#------------------------------------------------------------------------------
# Remove all but the files in the original distribution
#------------------------------------------------------------------------------

clean:
	- $(RM) $(CLEAN)

purge: distclean

distclean: clean
	- $(RM) camd_demo my_camd_demo.out
	- $(RM) camd_l_demo my_camd_l_demo.out
	- $(RM) camd_demo2 my_camd_demo2.out
	- $(RM) camd_simple my_camd_simple.out
	- $(RM) -r *.dSYM
