# Fiesta5_installation_note

*******************************************************************************
This is the installation note for FIESTA5 by A.V.Smirnov. 
*******************************************************************************

1. To get FIESTA5 installation pack, run:
 
   git clone https://bitbucket.org/feynmanIntegrals/fiesta.git 

2. Install dependencies: (for ubuntu)

apt-get install git g++ cmake zlib1g-dev libmpfr-dev gfortran libgsl0-dev

- for mpi user: apt-get install mpich
- for MMA interface: apt-get install qhull-bin
- for GPU version: apt-get install nvidia-cuda-toolkit nvidia-cuda-dev
- for build essential: apt-get install uuid-dev

Special note for CentOS users: one need to install those dependencies with theircertain correspondent with yum.

3. Run ./configure to produce paths.inc. And make sure you substitute the include path and library path for mpfr correctly. Especially when one is running on a cluster. 

****WARNING: MAKE SURE NOT TO RUN CONFIGURE AGAIN AFTER YOU CHANGE THE FILE****

4. Modify extra/Cuba-4.0/src/common/Parallel.c:

- Add "#include <sys/select.h>" to the preset section of this C file.

5. Go back to the FIESTA5 folder. run "make dep" to compile the dependencies.

6. Run "make" to compile the essential binaries for this package.

7. IMPORTANT: Copy every essential binary file below to FIESTA5/bin:

- CIntegrateMP from FIESTA5/real
- CIntegrateMPC from FIESTA5/complex
- CIntegrateMPG from FIESTA5/realG (for GPU version only)
- CIntegrateMPCG from FIESTA5/complexG (for GPU version only)
- CIntegratePool from FIESTA5/threads 
- CIntegratePoolMPI from FIESTA5/mpi (for MPI version only)
- CIntegrateTool from FIESTA5/sourcesTool
- KLink from FIESTA5/KLink

8. One can run "make test" and "make testmath" to test the installation.
If the test is OK, you are ready to go now. 
