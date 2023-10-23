FC = aarch64-linux-android-gfortran.exe
F77 = aarch64-linux-android-gfortran.exe

FFLAGS =  -pie -ffree-line-length-none -fdefault-integer-8

F77FLAGS = -pie -ffree-line-length-none -fdefault-integer-8

LAPACKPATH = ../../../libs-aarch64/liblapack.a

BLASPATH = ../../../libs-aarch64/libblas.a

LIB = $(LAPACKPATH) $(BLASPATH)

INC = -I../include/

OFLAG  = -O

# here it must not be main.o
SOURCE = ncoord.o gbobc.o asym.o atovlp.o axis2.o axis3.o axis.o blckmgs.o block.o blowsy.o cm5.o copyc6.o dftd3.o drsp.o dtrafo2.o dtrafo.o elem.o fermi.o foden.o fragment.o gauss.o iniq.o intpack.o dipole.o gover.o lin.o local.o lopt.o makel.o matinv.o molbld.o ncoord.o ncoord2.o neighbor.o onetri.o out.o pop.o pqn.o printbas.o printmold.o printmos.o prmat.o qsort.o rdcoord2.o readl2.o readl.o readparam.o setmetal.o setwll.o shifteps.o shiftlp.o spline2.o spline.o splitmol.o symtranslib.o timing.o uxtb.o warn.o wrc0.o wrcoord.o wren.o wrxyz.o xbasis.o xtb.o zmatpr.o
         
all:	libstda4xtb.a xtb4stda
         
libstda4xtb.a:	$(SOURCE)
	aarch64-linux-android-ar.exe qc libstda4xtb.a $(SOURCE)
	aarch64-linux-android-ranlib.exe libstda4xtb.a

xtb4stda:  main.o
#	$(FC) $(FFLAGS) $(SOURCE) $(LIB) -static-libgfortran -o xtb4stda
	$(FC) main.o -o xtb4stda ./libstda4xtb.a $(LIB) -pie
	aarch64-linux-android-strip.exe xtb4stda

clean: 
	-/bin/rm *.o *.a *~ *.mod xtb4stda

%.o: %.f
	$(FC) $(INC) $(F77FLAGS) $(OFLAG) -c $<

%.o: %.f90
	$(FC) $(INC) $(FFLAGS) $(OFLAG) -c $<
