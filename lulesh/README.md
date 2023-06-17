# Maestro Lulesh

Build the container:

```bash
$ docker build -t demo .
```

Shell in!

```bash
$ docker run -it demo bash
```

We have two examples in "study":

```bash
$ ls study/
```
```console
lulesh-flux-large.yaml  lulesh-flux.yaml
```

Try running lulesh with flux, headlessly! We aren't going to run the large problem
size (at least for me it freezes my computer!)

```bash
$ docker run -it demo flux start --test-size=4 maestro run study/lulesh-flux.yaml -y -fg
```

<details>

<summary>Output of Maestro</summary>

```console
[2023-06-17 03:25:14: INFO] INFO Logging Level -- Enabled
[2023-06-17 03:25:14: WARNING] WARNING Logging Level -- Enabled
[2023-06-17 03:25:14: CRITICAL] CRITICAL Logging Level -- Enabled
[2023-06-17 03:25:14: INFO] Loading specification -- path = study/lulesh-flux.yaml
[2023-06-17 03:25:14: INFO] Directory does not exist. Creating directories to /workflow/studies/lulesh/lulesh_sample1_20230617-032514/logs
[2023-06-17 03:25:14: INFO] Adding step 'make-lulesh' to study 'lulesh_sample1'...
[2023-06-17 03:25:14: INFO] Adding step 'run-lulesh' to study 'lulesh_sample1'...
[2023-06-17 03:25:14: INFO] run-lulesh is dependent on make-lulesh. Creating edge (make-lulesh, run-lulesh)...
[2023-06-17 03:25:14: INFO] 
------------------------------------------
Submission attempts =       1
Submission restart limit =  1
Submission throttle limit = 0
Use temporary directory =   False
Hash workspaces =           False
Dry run enabled =           False
Output path =               /workflow/studies/lulesh/lulesh_sample1_20230617-032514
------------------------------------------
[2023-06-17 03:25:14: INFO] Acquiring -- LULESH
[2023-06-17 03:25:14: INFO] Checking for connectivity to 'https://github.com/LLNL/LULESH.git'
[2023-06-17 03:25:15: INFO] Connectivity achieved!
[2023-06-17 03:25:15: INFO] Cloning 'LULESH' from 'https://github.com/LLNL/LULESH.git'...
[2023-06-17 03:25:16: INFO] Running Maestro Conductor in the foreground.
[2023-06-17 03:25:16: INFO] 
------------------------------------------
Submission attempts =       1
Submission throttle limit = 0
Use temporary directory =   False
Tmp Dir = 
------------------------------------------
[2023-06-17 03:25:16: INFO] 
==================================================
name: lulesh_sample1
description: A sample LULESH study that downloads, builds, and runs a parameter study of varying problem sizes and iterations on FLUX.
==================================================

[2023-06-17 03:25:16: INFO] 
==================================================
Constructing parameter study 'lulesh_sample1'
==================================================

[2023-06-17 03:25:16: INFO] 
==================================================
Processing step '_source'
==================================================

[2023-06-17 03:25:16: INFO] Encountered '_source'. Adding and continuing.
[2023-06-17 03:25:16: INFO] 
==================================================
Processing step 'make-lulesh'
==================================================

[2023-06-17 03:25:16: INFO] 
-------------------------------------------------
Adding step 'make-lulesh' (No parameters used)
-------------------------------------------------

[2023-06-17 03:25:16: INFO] Searching for workspaces...
cmd = cd /workflow/studies/lulesh/lulesh_sample1_20230617-032514/LULESH
mkdir build
cd build
cmake -WITH_MPI=Off -WITH_OPENMP=Off ..
make

[2023-06-17 03:25:16: INFO] 
==================================================
Processing step 'run-lulesh'
==================================================

[2023-06-17 03:25:16: INFO] 
==================================================
Expanding step 'run-lulesh'
==================================================
-------- Used Parameters --------
{'SIZE', 'ITERATIONS'}
---------------------------------
[2023-06-17 03:25:16: INFO] 
**********************************
Combo [SIZE.100.ITER.10]
**********************************
[2023-06-17 03:25:16: INFO] Searching for workspaces...
cmd = $(LAUNCHER) /workflow/studies/lulesh/lulesh_sample1_20230617-032514/LULESH/build/lulesh2.0 -s 100 -i 10 -p > SIZE.100.ITER.10.log

[2023-06-17 03:25:16: INFO] New cmd = $(LAUNCHER) /workflow/studies/lulesh/lulesh_sample1_20230617-032514/LULESH/build/lulesh2.0 -s 100 -i 10 -p > SIZE.100.ITER.10.log

[2023-06-17 03:25:16: INFO] Processing regular dependencies.
[2023-06-17 03:25:16: INFO] Adding edge (make-lulesh, run-lulesh_ITER.10.SIZE.100)...
[2023-06-17 03:25:16: INFO] 
**********************************
Combo [SIZE.100.ITER.20]
**********************************
[2023-06-17 03:25:16: INFO] Searching for workspaces...
cmd = $(LAUNCHER) /workflow/studies/lulesh/lulesh_sample1_20230617-032514/LULESH/build/lulesh2.0 -s 100 -i 20 -p > SIZE.100.ITER.20.log

[2023-06-17 03:25:16: INFO] New cmd = $(LAUNCHER) /workflow/studies/lulesh/lulesh_sample1_20230617-032514/LULESH/build/lulesh2.0 -s 100 -i 20 -p > SIZE.100.ITER.20.log

[2023-06-17 03:25:16: INFO] Processing regular dependencies.
[2023-06-17 03:25:16: INFO] Adding edge (make-lulesh, run-lulesh_ITER.20.SIZE.100)...
[2023-06-17 03:25:16: INFO] 
**********************************
Combo [SIZE.100.ITER.30]
**********************************
[2023-06-17 03:25:16: INFO] Searching for workspaces...
cmd = $(LAUNCHER) /workflow/studies/lulesh/lulesh_sample1_20230617-032514/LULESH/build/lulesh2.0 -s 100 -i 30 -p > SIZE.100.ITER.30.log

[2023-06-17 03:25:16: INFO] New cmd = $(LAUNCHER) /workflow/studies/lulesh/lulesh_sample1_20230617-032514/LULESH/build/lulesh2.0 -s 100 -i 30 -p > SIZE.100.ITER.30.log

[2023-06-17 03:25:16: INFO] Processing regular dependencies.
[2023-06-17 03:25:16: INFO] Adding edge (make-lulesh, run-lulesh_ITER.30.SIZE.100)...
[2023-06-17 03:25:16: INFO] Directory does not exist. Creating directories to /workflow/studies/lulesh/lulesh_sample1_20230617-032514/meta
[2023-06-17 03:25:16: INFO] Directory does not exist. Creating directories to /workflow/studies/lulesh/lulesh_sample1_20230617-032514/meta/study
[2023-06-17 03:25:16: INFO] Checking DAG status at 2023-06-17 03:25:16.181262
[2023-06-17 03:25:16: INFO] Jobs found for user 'root'.
[2023-06-17 03:25:16: INFO] Launching all ready steps...
[2023-06-17 03:25:16: INFO] Calling execute for StepRecord 'make-lulesh'
[2023-06-17 03:25:16: INFO] Directory does not exist. Creating directories to /workflow/studies/lulesh/lulesh_sample1_20230617-032514/make-lulesh
[2023-06-17 03:25:16: INFO] Generating script for make-lulesh into /workflow/studies/lulesh/lulesh_sample1_20230617-032514/make-lulesh
[2023-06-17 03:25:16: INFO] Running workflow step 'make-lulesh' locally.
[2023-06-17 03:25:16: INFO] Script: /workflow/studies/lulesh/lulesh_sample1_20230617-032514/make-lulesh/make-lulesh.flux.sh
Restart: None
Scheduled?: False
[2023-06-17 03:25:16: INFO] Attempting submission of 'make-lulesh' (attempt 1 of 1)...
[2023-06-17 03:25:18: INFO] Execution returned status OK.
[2023-06-17 03:25:20: INFO] Local step make-lulesh executed with status OK. Complete.
[2023-06-17 03:26:20: INFO] Checking DAG status at 2023-06-17 03:26:20.442924
[2023-06-17 03:26:20: INFO] Jobs found for user 'root'.
[2023-06-17 03:26:20: INFO] Launching all ready steps...
[2023-06-17 03:26:20: INFO] Calling execute for StepRecord 'run-lulesh_ITER.10.SIZE.100'
[2023-06-17 03:26:20: INFO] Directory does not exist. Creating directories to /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.10.SIZE.100
[2023-06-17 03:26:20: INFO] Generating script for run-lulesh_ITER.10.SIZE.100 into /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.10.SIZE.100
[2023-06-17 03:26:20: INFO] Scheduling workflow step 'run-lulesh_ITER.10.SIZE.100'.
[2023-06-17 03:26:20: INFO] Script: /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.10.SIZE.100/run-lulesh_ITER.10.SIZE.100.flux.sh
Restart: None
Scheduled?: True
[2023-06-17 03:26:20: INFO] Attempting submission of 'run-lulesh_ITER.10.SIZE.100' (attempt 1 of 1)...
Jun 17 03:26:20.689066 job-manager.err[0]: jobtap: job.new: callback returned error
[2023-06-17 03:26:20: INFO] Submission returned status OK. -- Assigned identifier (ƒWZ14gbR)
[2023-06-17 03:26:22: INFO] Calling execute for StepRecord 'run-lulesh_ITER.20.SIZE.100'
[2023-06-17 03:26:22: INFO] Directory does not exist. Creating directories to /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.20.SIZE.100
[2023-06-17 03:26:22: INFO] Generating script for run-lulesh_ITER.20.SIZE.100 into /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.20.SIZE.100
[2023-06-17 03:26:22: INFO] Scheduling workflow step 'run-lulesh_ITER.20.SIZE.100'.
[2023-06-17 03:26:22: INFO] Script: /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.20.SIZE.100/run-lulesh_ITER.20.SIZE.100.flux.sh
Restart: None
Scheduled?: True
[2023-06-17 03:26:22: INFO] Attempting submission of 'run-lulesh_ITER.20.SIZE.100' (attempt 1 of 1)...
Jun 17 03:26:22.465266 job-manager.err[0]: jobtap: job.new: callback returned error
[2023-06-17 03:26:22: INFO] Submission returned status OK. -- Assigned identifier (ƒXLJ8jxT)
[2023-06-17 03:26:23: INFO] Calling execute for StepRecord 'run-lulesh_ITER.30.SIZE.100'
[2023-06-17 03:26:23: INFO] Directory does not exist. Creating directories to /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.30.SIZE.100
[2023-06-17 03:26:23: INFO] Generating script for run-lulesh_ITER.30.SIZE.100 into /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.30.SIZE.100
[2023-06-17 03:26:23: INFO] Scheduling workflow step 'run-lulesh_ITER.30.SIZE.100'.
[2023-06-17 03:26:23: INFO] Script: /workflow/studies/lulesh/lulesh_sample1_20230617-032514/run-lulesh/ITER.30.SIZE.100/run-lulesh_ITER.30.SIZE.100.flux.sh
Restart: None
Scheduled?: True
[2023-06-17 03:26:23: INFO] Attempting submission of 'run-lulesh_ITER.30.SIZE.100' (attempt 1 of 1)...
Jun 17 03:26:23.842442 job-manager.err[0]: jobtap: job.new: callback returned error
[2023-06-17 03:26:23: INFO] Submission returned status OK. -- Assigned identifier (ƒXwBoqd9)
[2023-06-17 03:27:25: INFO] Checking DAG status at 2023-06-17 03:27:25.765087
[2023-06-17 03:27:25: INFO] Jobs found for user 'root'.
[2023-06-17 03:27:25: INFO] Step 'run-lulesh_ITER.20.SIZE.100' found to be running.
[2023-06-17 03:27:25: INFO] Step 'run-lulesh_ITER.10.SIZE.100' found to be running.
[2023-06-17 03:27:25: INFO] Step 'run-lulesh_ITER.30.SIZE.100' found to be running.
[2023-06-17 03:27:25: INFO] Launching all ready steps...
[2023-06-17 03:28:25: INFO] Checking DAG status at 2023-06-17 03:28:25.846751
[2023-06-17 03:28:25: INFO] Jobs found for user 'root'.
[2023-06-17 03:28:25: INFO] Step 'run-lulesh_ITER.20.SIZE.100' found to be running.
[2023-06-17 03:28:25: INFO] Step 'run-lulesh_ITER.10.SIZE.100' found to be running.
[2023-06-17 03:28:25: INFO] Step 'run-lulesh_ITER.30.SIZE.100' found to be running.
[2023-06-17 03:28:25: INFO] Launching all ready steps...
[2023-06-17 03:29:25: INFO] Checking DAG status at 2023-06-17 03:29:25.910674
[2023-06-17 03:29:25: INFO] Jobs found for user 'root'.
[2023-06-17 03:29:25: INFO] Step 'run-lulesh_ITER.20.SIZE.100' found to be running.
[2023-06-17 03:29:25: INFO] Step 'run-lulesh_ITER.10.SIZE.100' found to be running.
[2023-06-17 03:29:25: INFO] Step 'run-lulesh_ITER.30.SIZE.100' found to be running.
[2023-06-17 03:29:25: INFO] Launching all ready steps...
Jun 17 03:29:38.569815 job-manager.err[0]: jobtap: job.inactive-add: callback returned error
[2023-06-17 03:30:25: INFO] Checking DAG status at 2023-06-17 03:30:25.970669
[2023-06-17 03:30:25: INFO] Jobs found for user 'root'.
[2023-06-17 03:30:25: INFO] Step 'run-lulesh_ITER.20.SIZE.100' found to be running.
[2023-06-17 03:30:25: INFO] Step 'run-lulesh_ITER.10.SIZE.100' marked as finished. Adding to complete set.
[2023-06-17 03:30:25: INFO] Step 'run-lulesh_ITER.30.SIZE.100' found to be running.
[2023-06-17 03:30:25: INFO] Launching all ready steps...
[2023-06-17 03:31:26: INFO] Checking DAG status at 2023-06-17 03:31:26.034733
[2023-06-17 03:31:26: INFO] Jobs found for user 'root'.
[2023-06-17 03:31:26: INFO] Step 'run-lulesh_ITER.20.SIZE.100' found to be running.
[2023-06-17 03:31:26: INFO] Step 'run-lulesh_ITER.30.SIZE.100' found to be running.
[2023-06-17 03:31:26: INFO] Launching all ready steps...
[2023-06-17 03:32:26: INFO] Checking DAG status at 2023-06-17 03:32:26.094668
[2023-06-17 03:32:26: INFO] Jobs found for user 'root'.
[2023-06-17 03:32:26: INFO] Step 'run-lulesh_ITER.20.SIZE.100' found to be running.
[2023-06-17 03:32:26: INFO] Step 'run-lulesh_ITER.30.SIZE.100' found to be running.
[2023-06-17 03:32:26: INFO] Launching all ready steps...
Jun 17 03:32:28.347202 job-manager.err[0]: jobtap: job.inactive-add: callback returned error
Jun 17 03:32:53.723265 job-manager.err[0]: jobtap: job.inactive-add: callback returned error
[2023-06-17 03:33:26: INFO] Checking DAG status at 2023-06-17 03:33:26.154860
[2023-06-17 03:33:26: INFO] Jobs found for user 'root'.
[2023-06-17 03:33:26: INFO] Step 'run-lulesh_ITER.20.SIZE.100' marked as finished. Adding to complete set.
[2023-06-17 03:33:26: INFO] Step 'run-lulesh_ITER.30.SIZE.100' marked as finished. Adding to complete set.
[2023-06-17 03:33:26: INFO] Launching all ready steps...
[2023-06-17 03:33:26: INFO] 'lulesh_sample1' is complete. Returning.
```

You can ignore the job-manager jobtap errors - they happen because we are running Flux
with root (oups).

</details>

Try doing the same, but binding an output directory to save results to your machine.

```bash
$ mkdir -p ./studies
$ docker run -it -v $PWD/studies:/workflow/studies demo flux start --test-size=4 maestro run study/lulesh-flux.yaml -y -fg
```

And you can inspect the results directory!

<details>

<summary>Results Structure</summary>

```console
studies/
└── lulesh
    └── lulesh_sample1_20230617-040648
        ├── batch.info
        ├── logs
        │   └── lulesh_sample1.log
        ├── LULESH
        │   ├── build
        │   │   ├── CMakeCache.txt
        │   │   ├── CMakeFiles
        │   │   │   ├── 3.10.2
        │   │   │   │   ├── CMakeCXXCompiler.cmake
        │   │   │   │   ├── CMakeDetermineCompilerABI_CXX.bin
        │   │   │   │   ├── CMakeSystem.cmake
        │   │   │   │   └── CompilerIdCXX
        │   │   │   │       ├── a.out
        │   │   │   │       ├── CMakeCXXCompilerId.cpp
        │   │   │   │       └── tmp
        │   │   │   ├── cmake.check_cache
        │   │   │   ├── CMakeDirectoryInformation.cmake
        │   │   │   ├── CMakeOutput.log
        │   │   │   ├── CMakeTmp
        │   │   │   ├── feature_tests.bin
        │   │   │   ├── feature_tests.cxx
        │   │   │   ├── FindMPI
        │   │   │   │   ├── test_mpi.cpp
        │   │   │   │   └── test_mpi_CXX.bin
        │   │   │   ├── FindOpenMP
        │   │   │   │   ├── ompver_CXX.bin
        │   │   │   │   ├── OpenMPCheckVersion.cpp
        │   │   │   │   └── OpenMPTryFlag.cpp
        │   │   │   ├── lulesh2.0.dir
        │   │   │   │   ├── build.make
        │   │   │   │   ├── cmake_clean.cmake
        │   │   │   │   ├── CXX.includecache
        │   │   │   │   ├── DependInfo.cmake
        │   │   │   │   ├── depend.internal
        │   │   │   │   ├── depend.make
        │   │   │   │   ├── flags.make
        │   │   │   │   ├── link.txt
        │   │   │   │   ├── lulesh.cc.o
        │   │   │   │   ├── lulesh-comm.cc.o
        │   │   │   │   ├── lulesh-init.cc.o
        │   │   │   │   ├── lulesh-util.cc.o
        │   │   │   │   ├── lulesh-viz.cc.o
        │   │   │   │   └── progress.make
        │   │   │   ├── Makefile2
        │   │   │   ├── Makefile.cmake
        │   │   │   ├── progress.marks
        │   │   │   └── TargetDirectories.txt
        │   │   ├── cmake_install.cmake
        │   │   ├── lulesh2.0
        │   │   └── Makefile
        │   ├── CMakeLists.txt
        │   ├── lulesh.cc
        │   ├── lulesh-comm.cc
        │   ├── lulesh.h
        │   ├── lulesh-init.cc
        │   ├── lulesh_tuple.h
        │   ├── lulesh-util.cc
        │   ├── lulesh-viz.cc
        │   ├── Makefile
        │   ├── README
        │   └── TODO
        ├── lulesh-flux.yaml
        ├── lulesh_sample1.pkl
        ├── lulesh_sample1.study.pkl
        ├── make-lulesh
        │   ├── make-lulesh.169.err
        │   ├── make-lulesh.169.out
        │   └── make-lulesh.flux.sh
        ├── meta
        │   ├── environment.yaml
        │   ├── metadata.yaml
        │   ├── parameters.yaml
        │   └── study
        │       └── env.pkl
        ├── run-lulesh
        │   ├── ITER.10.SIZE.100
        │   │   ├── run-lulesh_ITER.10.SIZE.100.flux.sh
        │   │   ├── run-lulesh_ITER.10.SIZE.100.ƒYn1UBsm.err
        │   │   ├── run-lulesh_ITER.10.SIZE.100.ƒYn1UBsm.out
        │   │   └── SIZE.100.ITER.10.log
        │   ├── ITER.20.SIZE.100
        │   │   ├── run-lulesh_ITER.20.SIZE.100.flux.sh
        │   │   ├── run-lulesh_ITER.20.SIZE.100.ƒZPYCyb5.err
        │   │   ├── run-lulesh_ITER.20.SIZE.100.ƒZPYCyb5.out
        │   │   └── SIZE.100.ITER.20.log
        │   └── ITER.30.SIZE.100
        │       ├── run-lulesh_ITER.30.SIZE.100.flux.sh
        │       ├── run-lulesh_ITER.30.SIZE.100.ƒZuVkTsD.err
        │       ├── run-lulesh_ITER.30.SIZE.100.ƒZuVkTsD.out
        │       └── SIZE.100.ITER.30.log
        └── status.csv

20 directories, 73 files
```

</details>

We can inspect one of the *.log files in "run-lulesh":

```bash
$ cat studies/lulesh/lulesh_sample1_20230617-040648/run-lulesh/ITER.30.SIZE.100/SIZE.100.ITER.30.log 
Running problem size 100^3 per domain until completion
Num processors: 1
Num threads: 2
Total number of elements: 1000000 

To run other sizes, use -s <integer>.
To run a fixed number of iterations, use -i <integer>.
To run a more or less balanced region set, use -b <integer>.
To change the relative costs of regions, use -c <integer>.
To print out progress, use -p
To write an output file for VisIt, use -v
See help (-h) for more options

cycle = 1, time = 1.910718e-07, dt=1.910718e-07
cycle = 2, time = 4.203581e-07, dt=2.292862e-07
cycle = 3, time = 4.989486e-07, dt=7.859057e-08
cycle = 4, time = 5.645779e-07, dt=6.562923e-08
cycle = 5, time = 6.230838e-07, dt=5.850593e-08
cycle = 6, time = 6.774092e-07, dt=5.432541e-08
cycle = 7, time = 7.290587e-07, dt=5.164946e-08
cycle = 8, time = 7.789464e-07, dt=4.988778e-08
cycle = 9, time = 8.276916e-07, dt=4.874515e-08
cycle = 10, time = 8.757493e-07, dt=4.805775e-08
cycle = 11, time = 9.334186e-07, dt=5.766930e-08
cycle = 12, time = 9.985303e-07, dt=6.511161e-08
cycle = 13, time = 1.060082e-06, dt=6.155140e-08
cycle = 14, time = 1.118087e-06, dt=5.800581e-08
cycle = 15, time = 1.172544e-06, dt=5.445676e-08
cycle = 16, time = 1.224534e-06, dt=5.198930e-08
cycle = 17, time = 1.274973e-06, dt=5.043991e-08
cycle = 18, time = 1.324652e-06, dt=4.967896e-08
cycle = 19, time = 1.374324e-06, dt=4.967114e-08
cycle = 20, time = 1.423995e-06, dt=4.967114e-08
cycle = 21, time = 1.473666e-06, dt=4.967114e-08
cycle = 22, time = 1.523337e-06, dt=4.967114e-08
cycle = 23, time = 1.573008e-06, dt=4.967114e-08
cycle = 24, time = 1.627986e-06, dt=5.497832e-08
cycle = 25, time = 1.682965e-06, dt=5.497832e-08
cycle = 26, time = 1.737943e-06, dt=5.497832e-08
cycle = 27, time = 1.800609e-06, dt=6.266569e-08
cycle = 28, time = 1.863274e-06, dt=6.266569e-08
cycle = 29, time = 1.938109e-06, dt=7.483443e-08
cycle = 30, time = 2.023029e-06, dt=8.492029e-08
Run completed:
   Problem size        =  100
   MPI tasks           =  1
   Iteration count     =  30
   Final Origin Energy =  1.174431e+08
   Testing Plane 0 of Energy Array on rank 0:
        MaxAbsDiff   = 1.117587e-08
        TotalAbsDiff = 1.260178e-08
        MaxRelDiff   = 1.339561e-10

Elapsed time         =    3.5e+02 (s)
Grind time (us/z/c)  =  11.696606 (per dom)  ( 350.89819 overall)
FOM                  =  85.494884 (z/s)
```

Cool!

## Interactive Run

Now let's run the workflow with Flux! First shell into the container:

```bash
$ docker run -it demo bash
```

And start a Flux instance.
This targets the broker socket we have defined in our Maestro workflow.

```bash
$ flux start --test-size=4
```

Note that maestro will find the `FLUX_URI` in the environment.
Then run with Flux!

```bash
$ maestro run study/lulesh-flux.yaml -y
```

You can then get the status:

```bash
$ maestro status 
```
```console
# maestro status studies/lulesh/lulesh_sample1_20230323-031150/
                                                   Study: /workflow/studies/lulesh/lulesh_sample1_20230323-031150                                                   
┏━━━━━━━━━━━━━━━━━┳━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━┓
┃                 ┃        ┃                 ┃             ┃                ┃                ┃                 ┃                ┃                 ┃ Number         ┃
┃ Step Name       ┃ Job ID ┃ Workspace       ┃ State       ┃ Run Time       ┃ Elapsed Time   ┃ Start Time      ┃ Submit Time    ┃ End Time        ┃ Restarts       ┃
┡━━━━━━━━━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━┩
│ make-lulesh     │ 178    │ make-lulesh     │ FINISHED    │ 0d:00h:00m:03s │ 0d:00h:00m:03s │ 2023-03-23      │ 2023-03-23     │ 2023-03-23      │ 0              │
│                 │        │                 │             │                │                │ 03:12:04        │ 03:12:04       │ 03:12:07        │                │
│ run-lulesh_ITER │ --     │ run-lulesh/ITER │ INITIALIZED │ --:--:--       │ --:--:--       │ --              │ --             │ --              │ 0              │
│ .10.SIZE.100    │        │ .10.SIZE.100    │             │                │                │                 │                │                 │                │
│ run-lulesh_ITER │ --     │ run-lulesh/ITER │ INITIALIZED │ --:--:--       │ --:--:--       │ --              │ --             │ --              │ 0              │
│ .20.SIZE.100    │        │ .20.SIZE.100    │             │                │                │                 │                │                 │                │
│ run-lulesh_ITER │ --     │ run-lulesh/ITER │ INITIALIZED │ --:--:--       │ --:--:--       │ --              │ --             │ --              │ 0              │
│ .30.SIZE.100    │        │ .30.SIZE.100    │             │                │                │                 │                │                 │                │
└─────────────────┴────────┴─────────────────┴─────────────┴────────────────┴────────────────┴─────────────────┴────────────────┴─────────────────┴────────────────┘
```

Note that the jobs take a bit to submit - but you'll see them eventually with `flux jobs -a`
(I think lulesh needs to build first). They will go from running (R):

```bash
root@ff13d7344bcc:/workflow# flux jobs -a
```
```console
       JOBID USER     NAME       ST NTASKS NNODES     TIME INFO
    ƒd6B8zvb root     run-lules+  R      1      1   9.917s ff13d7344bcc
    ƒcY82XYB root     run-lules+  R      1      1   11.16s ff13d7344bcc
    ƒbiroRUb root     run-lules+  R      1      1   13.02s ff13d7344bcc
```

To completed (CD)!

```console
       JOBID USER     NAME       ST NTASKS NNODES     TIME INFO
   ƒ21y72C7H root     run-lules+ CD      1      1   5.968m 866992962d98
   ƒ218yPWTy root     run-lules+ CD      1      1   5.406m 866992962d98
    ƒzT9aoQj root     run-lules+ CD      1      1   2.847m 866992962d98
```

Also note there is an error/warning message when running flux with root - you can ignore for this demo.
When you see it, however, it indicates a flux job was submit!

```console
2023-03-23T03:13:10.411916Z job-manager.err[0]: jobtap: job.new: callback returned error
```

The command `flux job attach` can normally show you output, but in this case the workflow tool
redirects them to files. The same output files can be inspected in the "studies" directory
as we showed above. Next, let's exit from the flux instance and try running as the fluxuser.
This ideally should work for use in the flux operator.

```bash
# Make sure the fluxuser owns everything!
$ sudo chown -R fluxuser .

$ sudo -u fluxuser -E PATH=$PATH -E PYTHONPATH=$PYTHONPATH -E LD_LIBRARY_PATH=$LD_LIBRARY_PATH flux start --test-size=4
```

It's up to you, but I deleted the entire studies folder to start fresh, and then submit again:

```bash
$ rm -rf ./studies
$ maestro run study/lulesh-flux.yaml -y
$ maestro status ./studies/lulesh/lulesh_sample1_20230323-033808
```

The interaction should be the same as before, meaning it works with the flux user (without the root errors!)
When you are done, exit from the flux instance and container. Yer done!
