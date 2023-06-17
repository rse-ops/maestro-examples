# Maestro Hello World

These examples will show using Maestro to run a hello world example - one
using [Flux Framework](https://flux-framework.org) and one without. First, build the container:

```bash
$ docker build -t demo .
```

Here is how to run each, headlessly or non-interactively (this is important for automated setups).
First, let's use Flux.

```bash
# This command is going to use the maestro flux executor
$ docker run -it demo flux start --test-size=4 maestro run study/hello-world-flux.yaml -y -fg
```

<details>

```console
[2023-06-17 03:04:53: INFO] INFO Logging Level -- Enabled
[2023-06-17 03:04:53: WARNING] WARNING Logging Level -- Enabled
[2023-06-17 03:04:53: CRITICAL] CRITICAL Logging Level -- Enabled
[2023-06-17 03:04:53: INFO] Loading specification -- path = study/hello-world-flux.yaml
[2023-06-17 03:04:53: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/logs
[2023-06-17 03:04:53: INFO] Adding step 'hello' to study 'hello_world_multiparam'...
[2023-06-17 03:04:53: INFO] 
------------------------------------------
Submission attempts =       1
Submission restart limit =  1
Submission throttle limit = 0
Use temporary directory =   False
Hash workspaces =           False
Dry run enabled =           False
Output path =               /workflow/studies/hello_world/hello_world_multiparam_20230617-030453
------------------------------------------
[2023-06-17 03:04:53: INFO] Running Maestro Conductor in the foreground.
[2023-06-17 03:04:53: INFO] 
------------------------------------------
Submission attempts =       1
Submission throttle limit = 0
Use temporary directory =   False
Tmp Dir = 
------------------------------------------
[2023-06-17 03:04:53: INFO] 
==================================================
name: hello_world_multiparam
description: A simple multiparameter 'Hello World' study.
==================================================

[2023-06-17 03:04:53: INFO] 
==================================================
Constructing parameter study 'hello_world_multiparam'
==================================================

[2023-06-17 03:04:53: INFO] 
==================================================
Processing step '_source'
==================================================

[2023-06-17 03:04:53: INFO] Encountered '_source'. Adding and continuing.
[2023-06-17 03:04:53: INFO] 
==================================================
Processing step 'hello'
==================================================

[2023-06-17 03:04:53: INFO] 
==================================================
Expanding step 'hello'
==================================================
-------- Used Parameters --------
{'NAME', 'GREETING'}
---------------------------------
[2023-06-17 03:04:53: INFO] 
**********************************
Combo [NAME.Pam.GREETING.Hello]
**********************************
[2023-06-17 03:04:53: INFO] Searching for workspaces...
cmd = $(LAUNCHER) echo "Hello, Pam!" > Hello_Pam.txt

[2023-06-17 03:04:53: INFO] New cmd = $(LAUNCHER) echo "Hello, Pam!" > Hello_Pam.txt

[2023-06-17 03:04:53: INFO] 
**********************************
Combo [NAME.Jim.GREETING.Ciao]
**********************************
[2023-06-17 03:04:53: INFO] Searching for workspaces...
cmd = $(LAUNCHER) echo "Ciao, Jim!" > Ciao_Jim.txt

[2023-06-17 03:04:53: INFO] New cmd = $(LAUNCHER) echo "Ciao, Jim!" > Ciao_Jim.txt

[2023-06-17 03:04:53: INFO] 
**********************************
Combo [NAME.Michael.GREETING.Hey]
**********************************
[2023-06-17 03:04:53: INFO] Searching for workspaces...
cmd = $(LAUNCHER) echo "Hey, Michael!" > Hey_Michael.txt

[2023-06-17 03:04:53: INFO] New cmd = $(LAUNCHER) echo "Hey, Michael!" > Hey_Michael.txt

[2023-06-17 03:04:53: INFO] 
**********************************
Combo [NAME.Dwight.GREETING.Hi]
**********************************
[2023-06-17 03:04:53: INFO] Searching for workspaces...
cmd = $(LAUNCHER) echo "Hi, Dwight!" > Hi_Dwight.txt

[2023-06-17 03:04:53: INFO] New cmd = $(LAUNCHER) echo "Hi, Dwight!" > Hi_Dwight.txt

[2023-06-17 03:04:53: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/meta
[2023-06-17 03:04:53: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/meta/study
[2023-06-17 03:04:53: INFO] Checking DAG status at 2023-06-17 03:04:53.233586
[2023-06-17 03:04:53: INFO] Jobs found for user 'root'.
[2023-06-17 03:04:53: INFO] Launching all ready steps...
[2023-06-17 03:04:53: INFO] Calling execute for StepRecord 'hello_GREETING.Hello.NAME.Pam'
[2023-06-17 03:04:53: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hello.NAME.Pam
[2023-06-17 03:04:53: INFO] Generating script for hello_GREETING.Hello.NAME.Pam into /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hello.NAME.Pam
[2023-06-17 03:04:53: INFO] Running workflow step 'hello_GREETING.Hello.NAME.Pam' locally.
[2023-06-17 03:04:53: INFO] Script: /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hello.NAME.Pam/hello_GREETING.Hello.NAME.Pam.flux.sh
Restart: None
Scheduled?: False
[2023-06-17 03:04:53: INFO] Attempting submission of 'hello_GREETING.Hello.NAME.Pam' (attempt 1 of 1)...
[2023-06-17 03:04:53: INFO] Execution returned status OK.
[2023-06-17 03:04:54: INFO] Local step hello_GREETING.Hello.NAME.Pam executed with status OK. Complete.
[2023-06-17 03:04:54: INFO] Calling execute for StepRecord 'hello_GREETING.Ciao.NAME.Jim'
[2023-06-17 03:04:54: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Ciao.NAME.Jim
[2023-06-17 03:04:54: INFO] Generating script for hello_GREETING.Ciao.NAME.Jim into /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Ciao.NAME.Jim
[2023-06-17 03:04:54: INFO] Running workflow step 'hello_GREETING.Ciao.NAME.Jim' locally.
[2023-06-17 03:04:54: INFO] Script: /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Ciao.NAME.Jim/hello_GREETING.Ciao.NAME.Jim.flux.sh
Restart: None
Scheduled?: False
[2023-06-17 03:04:54: INFO] Attempting submission of 'hello_GREETING.Ciao.NAME.Jim' (attempt 1 of 1)...
[2023-06-17 03:04:54: INFO] Execution returned status OK.
[2023-06-17 03:04:56: INFO] Local step hello_GREETING.Ciao.NAME.Jim executed with status OK. Complete.
[2023-06-17 03:04:56: INFO] Calling execute for StepRecord 'hello_GREETING.Hey.NAME.Michael'
[2023-06-17 03:04:56: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hey.NAME.Michael
[2023-06-17 03:04:56: INFO] Generating script for hello_GREETING.Hey.NAME.Michael into /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hey.NAME.Michael
[2023-06-17 03:04:56: INFO] Running workflow step 'hello_GREETING.Hey.NAME.Michael' locally.
[2023-06-17 03:04:56: INFO] Script: /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hey.NAME.Michael/hello_GREETING.Hey.NAME.Michael.flux.sh
Restart: None
Scheduled?: False
[2023-06-17 03:04:56: INFO] Attempting submission of 'hello_GREETING.Hey.NAME.Michael' (attempt 1 of 1)...
[2023-06-17 03:04:56: INFO] Execution returned status OK.
[2023-06-17 03:04:58: INFO] Local step hello_GREETING.Hey.NAME.Michael executed with status OK. Complete.
[2023-06-17 03:04:58: INFO] Calling execute for StepRecord 'hello_GREETING.Hi.NAME.Dwight'
[2023-06-17 03:04:58: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hi.NAME.Dwight
[2023-06-17 03:04:58: INFO] Generating script for hello_GREETING.Hi.NAME.Dwight into /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hi.NAME.Dwight
[2023-06-17 03:04:58: INFO] Running workflow step 'hello_GREETING.Hi.NAME.Dwight' locally.
[2023-06-17 03:04:58: INFO] Script: /workflow/studies/hello_world/hello_world_multiparam_20230617-030453/hello/GREETING.Hi.NAME.Dwight/hello_GREETING.Hi.NAME.Dwight.flux.sh
Restart: None
Scheduled?: False
[2023-06-17 03:04:58: INFO] Attempting submission of 'hello_GREETING.Hi.NAME.Dwight' (attempt 1 of 1)...
[2023-06-17 03:04:58: INFO] Execution returned status OK.
[2023-06-17 03:04:59: INFO] Local step hello_GREETING.Hi.NAME.Dwight executed with status OK. Complete.
[2023-06-17 03:04:59: INFO] 'hello_world_multiparam' is complete. Returning.
```

</details>

Seeing this, we might try binding the expected output directory to see if we can save the results
to the host!

```bash
$ mkdir -p ./studies
$ docker run -it -v $PWD/studies:/workflow/studies demo flux start --test-size=4 maestro run study/hello-world-flux.yaml -y -fg
```

That seems to work! Ok this is great!

```console
── hello_world
    └── hello_world_multiparam_20230617-030700
        ├── batch.info
        ├── hello
        │   ├── GREETING.Ciao.NAME.Jim
        │   │   ├── Ciao_Jim.txt
        │   │   ├── hello_GREETING.Ciao.NAME.Jim.158.err
        │   │   ├── hello_GREETING.Ciao.NAME.Jim.158.out
        │   │   └── hello_GREETING.Ciao.NAME.Jim.flux.sh
        │   ├── GREETING.Hello.NAME.Pam
        │   │   ├── hello_GREETING.Hello.NAME.Pam.156.err
        │   │   ├── hello_GREETING.Hello.NAME.Pam.156.out
        │   │   ├── hello_GREETING.Hello.NAME.Pam.flux.sh
        │   │   └── Hello_Pam.txt
        │   ├── GREETING.Hey.NAME.Michael
        │   │   ├── hello_GREETING.Hey.NAME.Michael.160.err
        │   │   ├── hello_GREETING.Hey.NAME.Michael.160.out
        │   │   ├── hello_GREETING.Hey.NAME.Michael.flux.sh
        │   │   └── Hey_Michael.txt
        │   └── GREETING.Hi.NAME.Dwight
        │       ├── hello_GREETING.Hi.NAME.Dwight.162.err
        │       ├── hello_GREETING.Hi.NAME.Dwight.162.out
        │       ├── hello_GREETING.Hi.NAME.Dwight.flux.sh
        │       └── Hi_Dwight.txt
        ├── hello-world-flux.yaml
        ├── hello_world_multiparam.pkl
        ├── hello_world_multiparam.study.pkl
        ├── logs
        │   └── hello_world_multiparam.log
        ├── meta
        │   ├── environment.yaml
        │   ├── metadata.yaml
        │   ├── parameters.yaml
        │   └── study
        │       └── env.pkl
        └── status.csv

10 directories, 26 files
```

Now let's remove flux (and just run locally):

```bash
$ docker run -it demo maestro run study/hello-world.yaml -y -fg
```

We largely see the same output, but the difference is that we aren't submitting jobs to Flux.
Continue reading for how to run them interactively.

## Interactive

Here is a brief interactive example of doing the above, and showing you a few more commands
or ways to interact with Maestro. For the above, we used `-y` to say yes to prompts, and `-fg` to
run everything in the foreground. You don't have to do that, as we will see next.
First, shell in!

```bash
$ docker run -it demo bash
```

We have our two examples in "study":

```bash
$ ls study/
```
```console
hello-world-flux.yaml  hello-world.yaml
```

## Hello World without Flux

Let's first run the non Flux workflow to get a sense for Maestro. We use maestro run.

```bash
$ maestro run study/hello-world.yaml
```
It will ask you for a y/n to run the study (this can be forced with `-y`)

```console
[2023-03-23 01:22:48: INFO] INFO Logging Level -- Enabled
[2023-03-23 01:22:48: WARNING] WARNING Logging Level -- Enabled
[2023-03-23 01:22:48: CRITICAL] CRITICAL Logging Level -- Enabled
[2023-03-23 01:22:48: INFO] Loading specification -- path = study/hello-world-multi.yaml
[2023-03-23 01:22:48: INFO] Directory does not exist. Creating directories to /workflow/studies/hello_world/hello_world_multiparam_20230323-012248/logs
[2023-03-23 01:22:48: INFO] Adding step 'hello' to study 'hello_world_multiparam'...
[2023-03-23 01:22:48: INFO] 
------------------------------------------
Submission attempts =       1
Submission restart limit =  1
Submission throttle limit = 0
Use temporary directory =   False
Hash workspaces =           False
Dry run enabled =           False
Output path =               /workflow/studies/hello_world/hello_world_multiparam_20230323-012248
------------------------------------------
Would you like to launch the study? [yn] y
Study launched successfully.
```

After you say yes, it won't hang on the submit - it will return to the terminal. You will need to explicitly ask for 
a status, and point that at the study folder, which will be present now in `studies`:

```bash
$ maestro status studies/hello_world/hello_world_multiparam_20230323-012248/
                                                  Study: /workflow/studies/hello_world/hello_world_multiparam_20230323-012248                                                   
┏━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━┳━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━┓
┃ Step Name          ┃ Job ID ┃ Workspace         ┃ State    ┃ Run Time       ┃ Elapsed Time   ┃ Start Time         ┃ Submit Time       ┃ End Time           ┃ Number Restarts ┃
┡━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━┩
│ hello_GREETING.Hel │ 16     │ hello/GREETING.He │ FINISHED │ 0d:00h:00m:01s │ 0d:00h:00m:01s │ 2023-03-23         │ 2023-03-23        │ 2023-03-23         │ 0               │
│ lo.NAME.Pam        │        │ llo.NAME.Pam      │          │                │                │ 01:22:51           │ 01:22:51          │ 01:22:52           │                 │
│ hello_GREETING.Cia │ 17     │ hello/GREETING.Ci │ FINISHED │ 0d:00h:00m:02s │ 0d:00h:00m:02s │ 2023-03-23         │ 2023-03-23        │ 2023-03-23         │ 0               │
│ o.NAME.Jim         │        │ ao.NAME.Jim       │          │                │                │ 01:22:52           │ 01:22:52          │ 01:22:54           │                 │
│ hello_GREETING.Hey │ 18     │ hello/GREETING.He │ FINISHED │ 0d:00h:00m:01s │ 0d:00h:00m:01s │ 2023-03-23         │ 2023-03-23        │ 2023-03-23         │ 0               │
│ .NAME.Michael      │        │ y.NAME.Michael    │          │                │                │ 01:22:54           │ 01:22:54          │ 01:22:55           │                 │
│ hello_GREETING.Hi. │ 19     │ hello/GREETING.Hi │ FINISHED │ 0d:00h:00m:01s │ 0d:00h:00m:01s │ 2023-03-23         │ 2023-03-23        │ 2023-03-23         │ 0               │
│ NAME.Dwight        │        │ .NAME.Dwight      │          │                │                │ 01:22:55           │ 01:22:55          │ 01:22:56           │                 │
└────────────────────┴────────┴───────────────────┴──────────┴────────────────┴────────────────┴────────────────────┴───────────────────┴────────────────────┴─────────────────┘
```

And that's the hello-world example! We will hopefully be adding new (more complex) examples soon.
