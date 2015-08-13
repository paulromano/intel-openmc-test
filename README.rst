--------------------------------------------
Reactor Benchmark Problem for OpenMC Testing
--------------------------------------------

**Prerequisites**: Fortran compiler, CMake, git, Python 2.7+

This repository contains four versions of the Hoogenboom-Martin pressurized
water reactor benchmark problem. Two versions use the original material
specification from the benchmark (small), and two other versions use a modified
version where the fuel material includes over 400 nuclides (large). For each of
the small and large models, there are two variants with and without tallies.

*Note*: The final case (large-tallies) requires over 3 GB of memory and as a
result may not run on some systems.

There are three scripts that can be used to set up OpenMC and its required cross
section data, run the test problems, and collect results. The scripts are as
follows:

1. ``setup`` -- a bash shell script which 'git clone's the OpenMC repository
   from GitHub, uses a Python script within the OpenMC distribution to download
   cross section data, and then uses CMake along with a Fortran compiler to
   build the OpenMC executable

2. ``run-tests`` -- a bash shell script which uses the downloaded cross sections
   and the OpenMC executable to run the four different test cases

3. ``collect-results`` -- a bash shell script which determines the performance
   of each of the four test cases and displays it. The measure used is the
   number of particles simulated per second during active batches.
