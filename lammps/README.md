# Maestro LAMMPS

Build the container:

```bash
$ docker build -t demo .
```

We have two examples in "study"

```bash
$ ls study/
```
```console
lammps-flux.yaml  lammps.yaml
```

Note that we currently don't have a flux version working because the maestro version is mismatched.
I've reported this issue [here](https://github.com/LLNL/maestrowf/issues/421). Try running LAMMPS, first headlessly.

```bash
$ docker run -it demo maestro run study/lammps.yaml -y -fg
```

or binding the output directory to see output:

```bash
$ mkdir -p studies
$ docker run -it -v $PWD/studies:/workflow/studies demo maestro run study/lammps.yaml -y -fg
```

<details>

<summary>Output of Maestro</summary>

```console
[2023-06-17 19:47:38: INFO] INFO Logging Level -- Enabled
[2023-06-17 19:47:38: WARNING] WARNING Logging Level -- Enabled
[2023-06-17 19:47:38: CRITICAL] CRITICAL Logging Level -- Enabled
[2023-06-17 19:47:38: INFO] Loading specification -- path = study/lammps.yaml
[2023-06-17 19:47:38: INFO] Directory does not exist. Creating directories to /workflow/studies/lammps/lammps_sample1_20230617-194738/logs
[2023-06-17 19:47:38: INFO] Adding step 'run-lammps' to study 'lammps_sample1'...
[2023-06-17 19:47:38: INFO] 
------------------------------------------
Submission attempts =       1
Submission restart limit =  1
Submission throttle limit = 0
Use temporary directory =   False
Hash workspaces =           False
Dry run enabled =           False
Output path =               /workflow/studies/lammps/lammps_sample1_20230617-194738
------------------------------------------
[2023-06-17 19:47:38: INFO] Running Maestro Conductor in the foreground.
[2023-06-17 19:47:38: INFO] 
------------------------------------------
Submission attempts =       1
Submission throttle limit = 0
Use temporary directory =   False
Tmp Dir = 
------------------------------------------
[2023-06-17 19:47:38: INFO] 
==================================================
name: lammps_sample1
description: A sample maestro working running lammps in the container across a small set of problem sizes.
==================================================

[2023-06-17 19:47:38: INFO] 
==================================================
Constructing parameter study 'lammps_sample1'
==================================================

[2023-06-17 19:47:38: INFO] 
==================================================
Processing step '_source'
==================================================

[2023-06-17 19:47:38: INFO] Encountered '_source'. Adding and continuing.
[2023-06-17 19:47:38: INFO] 
==================================================
Processing step 'run-lammps'
==================================================

[2023-06-17 19:47:38: INFO] 
==================================================
Expanding step 'run-lammps'
==================================================
-------- Used Parameters --------
{'X', 'Y', 'Z'}
---------------------------------
[2023-06-17 19:47:38: INFO] 
**********************************
Combo [X.1.Y.1.Z.1]
**********************************
[2023-06-17 19:47:38: INFO] Searching for workspaces...
cmd = cd /home/flux/examples/reaxff/HNS
# Don't run as root, kids
export OMPI_ALLOW_RUN_AS_ROOT=1
export OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1
mpirun -np 2 --map-by socket lmp -v x 1 -v y 1 -v z 1 -in in.reaxc.hns -nocite

[2023-06-17 19:47:38: INFO] New cmd = cd /home/flux/examples/reaxff/HNS
# Don't run as root, kids
export OMPI_ALLOW_RUN_AS_ROOT=1
export OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1
mpirun -np 2 --map-by socket lmp -v x 1 -v y 1 -v z 1 -in in.reaxc.hns -nocite

[2023-06-17 19:47:38: INFO] 
**********************************
Combo [X.2.Y.2.Z.2]
**********************************
[2023-06-17 19:47:38: INFO] Searching for workspaces...
cmd = cd /home/flux/examples/reaxff/HNS
# Don't run as root, kids
export OMPI_ALLOW_RUN_AS_ROOT=1
export OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1
mpirun -np 2 --map-by socket lmp -v x 2 -v y 2 -v z 2 -in in.reaxc.hns -nocite

[2023-06-17 19:47:38: INFO] New cmd = cd /home/flux/examples/reaxff/HNS
# Don't run as root, kids
export OMPI_ALLOW_RUN_AS_ROOT=1
export OMPI_ALLOW_RUN_AS_ROOT_CONFIRM=1
mpirun -np 2 --map-by socket lmp -v x 2 -v y 2 -v z 2 -in in.reaxc.hns -nocite

[2023-06-17 19:47:38: INFO] Directory does not exist. Creating directories to /workflow/studies/lammps/lammps_sample1_20230617-194738/meta
[2023-06-17 19:47:38: INFO] Directory does not exist. Creating directories to /workflow/studies/lammps/lammps_sample1_20230617-194738/meta/study
[2023-06-17 19:47:38: INFO] Checking DAG status at 2023-06-17 19:47:38.186854
[2023-06-17 19:47:38: INFO] No jobs found.
[2023-06-17 19:47:38: INFO] Launching all ready steps...
[2023-06-17 19:47:38: INFO] Calling execute for StepRecord 'run-lammps_X.1.Y.1.Z.1'
[2023-06-17 19:47:38: INFO] Directory does not exist. Creating directories to /workflow/studies/lammps/lammps_sample1_20230617-194738/run-lammps/X.1.Y.1.Z.1
[2023-06-17 19:47:38: INFO] Generating script for run-lammps_X.1.Y.1.Z.1 into /workflow/studies/lammps/lammps_sample1_20230617-194738/run-lammps/X.1.Y.1.Z.1
[2023-06-17 19:47:38: INFO] Script: /workflow/studies/lammps/lammps_sample1_20230617-194738/run-lammps/X.1.Y.1.Z.1/run-lammps_X.1.Y.1.Z.1.sh
Restart: None
Scheduled?: False
[2023-06-17 19:47:38: INFO] Attempting submission of 'run-lammps_X.1.Y.1.Z.1' (attempt 1 of 1)...
[2023-06-17 19:47:44: INFO] Execution returned status OK.
[2023-06-17 19:47:46: INFO] Local step run-lammps_X.1.Y.1.Z.1 executed with status OK. Complete.
[2023-06-17 19:47:46: INFO] Calling execute for StepRecord 'run-lammps_X.2.Y.2.Z.2'
[2023-06-17 19:47:46: INFO] Directory does not exist. Creating directories to /workflow/studies/lammps/lammps_sample1_20230617-194738/run-lammps/X.2.Y.2.Z.2
[2023-06-17 19:47:46: INFO] Generating script for run-lammps_X.2.Y.2.Z.2 into /workflow/studies/lammps/lammps_sample1_20230617-194738/run-lammps/X.2.Y.2.Z.2
[2023-06-17 19:47:46: INFO] Script: /workflow/studies/lammps/lammps_sample1_20230617-194738/run-lammps/X.2.Y.2.Z.2/run-lammps_X.2.Y.2.Z.2.sh
Restart: None
Scheduled?: False
[2023-06-17 19:47:46: INFO] Attempting submission of 'run-lammps_X.2.Y.2.Z.2' (attempt 1 of 1)...
[2023-06-17 19:47:59: INFO] Execution returned status OK.
[2023-06-17 19:48:01: INFO] Local step run-lammps_X.2.Y.2.Z.2 executed with status OK. Complete.
[2023-06-17 19:48:01: INFO] 'lammps_sample1' is complete. Returning.
```

You can ignore the job-manager jobtap errors - they happen because we are running Flux
with root (oups).

</details>

Here is the example output structure:

```bash
studies/
└── lammps
    └── lammps_sample1_20230617-055910
        ├── batch.info
        ├── lammps_sample1.pkl
        ├── lammps_sample1.study.pkl
        ├── lammps.yaml
        ├── logs
        │   └── lammps_sample1.log
        ├── meta
        │   ├── environment.yaml
        │   ├── metadata.yaml
        │   ├── parameters.yaml
        │   └── study
        │       └── env.pkl
        ├── run-lammps
        │   ├── X.1.Y.1.Z.1
        │   │   ├── run-lammps_X.1.Y.1.Z.1.16.err
        │   │   ├── run-lammps_X.1.Y.1.Z.1.16.out
        │   │   └── run-lammps_X.1.Y.1.Z.1.sh
        │   └── X.2.Y.2.Z.2
        │       ├── run-lammps_X.2.Y.2.Z.2.24.err
        │       ├── run-lammps_X.2.Y.2.Z.2.24.out
        │       └── run-lammps_X.2.Y.2.Z.2.sh
        └── status.csv

8 directories, 16 files
```

And you can peek into a *.out file to see output:

```bash
$ cat studies/lammps/lammps_sample1_20230617-194738/run-lammps/X.2.Y.2.Z.2/run-lammps_X.2.Y.2.Z.2.27.out 
```
```console
LAMMPS (29 Sep 2021 - Update 2)
OMP_NUM_THREADS environment is not set. Defaulting to 1 thread. (src/comm.cpp:98)
  using 1 OpenMP thread(s) per MPI task
Reading data file ...
  triclinic box = (0.0000000 0.0000000 0.0000000) to (22.326000 11.141200 13.778966) with tilt (0.0000000 -5.0260300 0.0000000)
  2 by 1 by 1 MPI processor grid
  reading atoms ...
  304 atoms
  reading velocities ...
  304 velocities
  read_data CPU = 0.002 seconds
Replicating atoms ...
  triclinic box = (0.0000000 0.0000000 0.0000000) to (44.652000 22.282400 27.557932) with tilt (0.0000000 -10.052060 0.0000000)
  2 by 1 by 1 MPI processor grid
  bounding box image = (0 -1 -1) to (0 1 1)
  bounding box extra memory = 0.03 MB
  average # of replicas added to proc = 5.00 out of 8 (62.50%)
  2432 atoms
  replicate CPU = 0.001 seconds
Neighbor list info ...
  update every 20 steps, delay 0 steps, check no
  max neighbors/atom: 2000, page size: 100000
  master list distance cutoff = 11
  ghost atom cutoff = 11
  binsize = 5.5, bins = 10 5 6
  2 neighbor lists, perpetual/occasional/extra = 2 0 0
  (1) pair reax/c, perpetual
      attributes: half, newton off, ghost
      pair build: half/bin/newtoff/ghost
      stencil: full/ghost/bin/3d
      bin: standard
  (2) fix qeq/reax, perpetual, copy from (1)
      attributes: half, newton off, ghost
      pair build: copy
      stencil: none
      bin: none
Setting up Verlet run ...
  Unit style    : real
  Current step  : 0
  Time step     : 0.1
Per MPI rank memory allocation (min/avg/max) = 143.9 | 143.9 | 143.9 Mbytes
Step Temp PotEng Press E_vdwl E_coul Volume 
       0          300   -113.27833    437.52118   -111.57687   -1.7014647    27418.867 
      10    299.38517   -113.27631    1439.2824   -111.57492   -1.7013813    27418.867 
      20    300.27107   -113.27884     3764.342   -111.57762   -1.7012247    27418.867 
      30    302.21063   -113.28428    7007.6629   -111.58335   -1.7009363    27418.867 
      40    303.52265   -113.28799    9844.8245   -111.58747   -1.7005186    27418.867 
      50    301.87059   -113.28324    9663.0973   -111.58318   -1.7000523    27418.867 
      60    296.67807   -113.26777    7273.8119   -111.56815   -1.6996137    27418.867 
      70    292.19999   -113.25435    5533.5522   -111.55514   -1.6992158    27418.867 
      80    293.58677   -113.25831    5993.4438   -111.55946   -1.6988533    27418.867 
      90    300.62635   -113.27925    7202.8369   -111.58069   -1.6985592    27418.867 
     100    305.38276   -113.29357    10085.805   -111.59518   -1.6983874    27418.867 
Loop time of 12.3226 on 2 procs for 100 steps with 2432 atoms

Performance: 0.070 ns/day, 342.295 hours/ns, 8.115 timesteps/s
99.7% CPU use with 2 MPI tasks x 1 OpenMP threads

MPI task timing breakdown:
Section |  min time  |  avg time  |  max time  |%varavg| %total
---------------------------------------------------------------
Pair    | 8.6019     | 8.9134     | 9.2249     |  10.4 | 72.33
Neigh   | 0.26016    | 0.26047    | 0.26079    |   0.1 |  2.11
Comm    | 0.011804   | 0.3234     | 0.635      |  54.8 |  2.62
Output  | 0.00024133 | 0.00030742 | 0.00037351 |   0.0 |  0.00
Modify  | 2.8239     | 2.8241     | 2.8243     |   0.0 | 22.92
Other   |            | 0.0009078  |            |       |  0.01

Nlocal:        1216.00 ave        1216 max        1216 min
Histogram: 2 0 0 0 0 0 0 0 0 0
Nghost:        7591.50 ave        7597 max        7586 min
Histogram: 1 0 0 0 0 0 0 0 0 1
Neighs:        432912.0 ave      432942 max      432882 min
Histogram: 1 0 0 0 0 0 0 0 0 1

Total # of neighbors = 865824
Ave neighs/atom = 356.01316
Neighbor list builds = 5
Dangerous builds not checked
Total wall time: 0:00:12
```
