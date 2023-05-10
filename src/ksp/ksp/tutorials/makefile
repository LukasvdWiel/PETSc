-include ../../../../petscdir.mk
CFLAGS           =
FFLAGS           =
CPPFLAGS         =
FPPFLAGS         =
LOCDIR           = src/ksp/ksp/tutorials/
DIRS             = network
EXAMPLESC        = ex001.c ex002.c ex003.c ex004.c ex005.c ex006.c ex007.c ex008.c ex009.c \
                   ex010.c ex011.c ex012.c ex013.c ex015.c ex016.c ex018.c ex021.c ex023.c \
                   ex025.c ex027.c ex028.c ex029.c ex032.c ex034.c \
                   ex041.c ex042.c ex043.c \
                   ex045.c ex046.c ex049.c ex050.c ex051.c ex052.c ex053.c \
                   ex054.c ex055.c ex056.c ex059.c ex062.c ex064.c ex065.c ex066.c \
                   ex067.c ex068.c ex069.c ex070.c ex071.c ex072.c ex073.c ex074.c ex075.c ex076.c ex077.c ex078.c ex079.c ex100.c
EXAMPLESF        = ex001.F90 ex002.F90 ex006.F90 ex011.F90 ex013.F90 ex014.F90 ex015.F90 ex022.F90 ex044.F90 ex045.F90 \
                   ex005.F90 ex052.F90 ex054.F90 ex061.F90 ex007.F90 ex100.F90 ex075.F90 ex076.F90 ex077.F90
MANSEC           = KSP
CLEANFILES       = rhs.vtk solution.vtk
NP               = 1
DIRS             = amrex

include ${PETSC_DIR}/lib/petsc/conf/variables
include ${PETSC_DIR}/lib/petsc/conf/rules

testex100: ex100.PETSc
	-@if [ "${PETSC_WITH_BATCH}" != "" ]; then \
           echo "Running with batch filesystem; to test run src/ksp/ksp/tutorials/ex100 with" ; \
           echo "your systems batch system"; \
        elif [ "${MPIEXEC}" = "/bin/false" ]; then \
           echo "*mpiexec not found*. Please run src/ksp/ksp/tutorials/ex100 manually"; \
	elif [ -f ex100 ]; then \
           ${MPIEXEC} -n 1 ./ex100 -test  > ex100_1.tmp 2>&1; \
	   if (${DIFF} output/ex100_1.testout ex100_1.tmp > /dev/null 2>&1) then \
           echo "C/C++ Python example src/ksp/ksp/tutorials/ex100 run successfully with 1 MPI process"; \
	   else echo "Possible error running C/C++ Python src/ksp/ksp/tutorials/ex100 with 1 MPI process"; \
           echo "See http://www.mcs.anl.gov/petsc/documentation/faq.html";\
           cat ex100_1.tmp; fi; \
        ${RM} -f ex100_1.tmp; fi

include ${PETSC_DIR}/lib/petsc/conf/test
