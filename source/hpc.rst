HPC
===========================================

Install SPECFEM3D in WSL2
---------------------------

Use openmpi installed by ``sudo apt-get install openmpi-bin libopenmpi-dev``, then run:

.. code-block:: bash

 $: ./configure FC=gfortran CC=gcc MPIFC=mpif90 --with-mpi

The configure fails with:

.. code-block:: bash

 $: Cannot open configuration file /deps/petsc-3.16.4/share/openmpi/mpif90-wrapper-data.txt
 $: Error parsing data file mpif90: Not found
 $: checking for mpi.h... no
 $: configure: error: MPI header not found; try setting MPI_INC.

Solve the problem by

