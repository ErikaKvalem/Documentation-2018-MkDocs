# Terminal code for cbcbeat installation. 

## First part of the installation  

```
Erikas-MacBook-Air:Desktop erikakvalem$ cd meg-cbcbeat-370fa4c4a62e/
Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ sudo python setup.py install
Password:
running install
running build
running build_py
creating build
creating build/lib
creating build/lib/cbcbeat
copying cbcbeat/cardiacmodels.py -> build/lib/cbcbeat
copying cbcbeat/splittingsolver.py -> build/lib/cbcbeat
copying cbcbeat/markerwisefield.py -> build/lib/cbcbeat
copying cbcbeat/monodomainsolver.py -> build/lib/cbcbeat
copying cbcbeat/gotran2dolfin.py -> build/lib/cbcbeat
copying cbcbeat/cellsolver.py -> build/lib/cbcbeat
copying cbcbeat/dolfinimport.py -> build/lib/cbcbeat
copying cbcbeat/__init__.py -> build/lib/cbcbeat
copying cbcbeat/bidomainsolver.py -> build/lib/cbcbeat
copying cbcbeat/gotran2cellmodel.py -> build/lib/cbcbeat
copying cbcbeat/gossplittingsolver.py -> build/lib/cbcbeat
copying cbcbeat/utils.py -> build/lib/cbcbeat
creating build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/tentusscher_2004_mcell_disc.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/fitzhughnagumo.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/fitzhughnagumo_manual.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/rogers_mcculloch_manual.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/fenton_karma_1998_MLR1_altered.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/__init__.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/beeler_reuter_1977.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/fenton_karma_1998_BR_altered.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/tentusscher_2004_mcell_cont.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/tentusscher_panfilov_2006_M_cell.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/tentusscher_2004_mcell.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/grandi_pasqualini_bers_2010.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/cardiaccellmodel.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/nocellmodel.py -> build/lib/cbcbeat/cellmodels
copying cbcbeat/cellmodels/tentusscher_panfilov_2006_epi_cell.py -> build/lib/cbcbeat/cellmodels
running build_scripts
creating build/scripts-2.7
copying and adjusting scripts/gotran2beat -> build/scripts-2.7
copying and adjusting scripts/gotran2dolfin -> build/scripts-2.7
changing mode of build/scripts-2.7/gotran2beat from 644 to 755
changing mode of build/scripts-2.7/gotran2dolfin from 644 to 755
running install_lib
running install_scripts
copying build/scripts-2.7/gotran2beat -> /Library/Frameworks/Python.framework/Versions/2.7/bin
copying build/scripts-2.7/gotran2dolfin -> /Library/Frameworks/Python.framework/Versions/2.7/bin
changing mode of /Library/Frameworks/Python.framework/Versions/2.7/bin/gotran2beat to 755
changing mode of /Library/Frameworks/Python.framework/Versions/2.7/bin/gotran2dolfin to 755
running install_egg_info
Removing /Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/cbcbeat-1.0-py2.7.egg-info
Writing /Library/Frameworks/Python.framework/Versions/2.7/lib/python2.7/site-packages/cbcbeat-1.0-py2.7.egg-info
**Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ export PYTHONPATH=`pwd`:$PYTHONPATH**
**Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ ls**
AUTHORS			bitbucket-pipelines.yml	joss
COPYING			build			sandbox
COPYING.LESSER		cbcbeat			scripts
Dockerfile		data			setup.py
INSTALL			demo			test
README.rst		doc
**Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ cd demo**
**Erikas-MacBook-Air:demo erikakvalem$ ls**
README.rst		generate-new-cell-model	niederer-benchmark
bidomain-biventricular	monodomain		single-cell-model
cardiac-ode-solver	multi-cell-model
**Erikas-MacBook-Air:demo erikakvalem$ cd ..**
**Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ ls**
AUTHORS			bitbucket-pipelines.yml	joss
COPYING			build			sandbox
COPYING.LESSER		cbcbeat			scripts
Dockerfile		data			setup.py
INSTALL			demo			test
README.rst		doc
**Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ cd test**
**Erikas-MacBook-Air:test erikakvalem$ ls**
README		conftest.py	unit
**Erikas-MacBook-Air:test erikakvalem$ py.test -m "fast" -v**
-bash: py.test: command not found
**Erikas-MacBook-Air:test erikakvalem$ cat README**
Collection of tests for cbcbeat
===================================

Running the tests:
------------------

We recommend running the tests from the test/unit/ directory. The complete
test suite can be run with:

  py.test

For quick testing, we recommend:

  py.test -m "not slow" -v

For testing with only FEniCS and not dolfin-adjoint installed, run:

  py.test -m "not adjoint" -v

For parallel run install python-pytest-xdist.
Enable the xdist plugin by:

  py.test -n N

where N is the number of cores to be used.

To see the standard output of the tests, as well as for dropping into an
debugger or embedded IPython shell you want to use:

  py.test -s

Guidelines for organizing the tests:
----------------------------------------

- Mark tests that tests dolfin-adjoint functionality by

  @adjoint

- Mark tests according to speed:

  @fast   : (complete) test < ~1 s
  @medium : (complete) test < ~10 s
  @slow   : (complete) test > ~10 s
**Erikas-MacBook-Air:test erikakvalem$ cd unit**
**Erikas-MacBook-Air:unit erikakvalem$ ls**
Vm_reference.npy			test_cellmodels.py
derive_analytic_bidomain.py		test_cellsolvers_long.py
long_references				test_fitzhugh_vs_pycc.py
test_analytic_bidomain.py		test_merger.py
test_basicsinglecellsolver.py		test_odepde.py
test_basicsinglecellsolver_adjoint.py	test_pdesolvers.py
test_basicsinglecellsolver_long.py	test_splitting_with_domains.py
test_bidomainsolver.py			test_splittingsolvers.py
test_bidomainsolvers_adjoint.py		test_splittingsolvers_adjoint.py
test_cardiacodesolver.py		testutils.py
test_cardiacodesolver_adjoint.py
**Erikas-MacBook-Air:unit erikakvalem$ cd ..**
**Erikas-MacBook-Air:test erikakvalem$ cd ..**
**Erikas-MacBook-Air:meg-cbcbeat-370fa4c4a62e erikakvalem$ ls**
AUTHORS			bitbucket-pipelines.yml	joss
COPYING			build			sandbox
COPYING.LESSER		cbcbeat			scripts
Dockerfile		data			setup.py
INSTALL			demo			test
README.rst		doc
```

## Second part of the installation
```

**fenics@0ca36cf2dd4f:~/local$ sudo apt-get install openssh-client**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version (1:7.2p2-4ubuntu2.2).
openssh-client set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**fenics@0ca36cf2dd4f:~/local$ ssh**
usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] [user@]hostname [command]
**fenics@0ca36cf2dd4f:~/local$ sudo apt-get update**
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial InRelease [247 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main Sources [154 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/restricted Sources [2243 B]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/universe Sources [81.2 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/multiverse Sources [2129 B]                 
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [639 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial/main Sources [1103 kB]                               
Get:11 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages [12.7 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [445 kB]           
Get:13 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [3743 B]         
Get:14 http://archive.ubuntu.com/ubuntu xenial/restricted Sources [5179 B]                          
Get:15 http://archive.ubuntu.com/ubuntu xenial/universe Sources [9802 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial/multiverse Sources [215 kB]           
Get:17 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1558 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [14.1 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [9827 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [176 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial-updates/main Sources [387 kB]
Get:22 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Sources [2684 B]
Get:23 http://archive.ubuntu.com/ubuntu xenial-updates/universe Sources [256 kB]
Get:24 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Sources [9026 B]
Get:25 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [1014 kB]
Get:26 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages [13.1 kB]
Get:27 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [814 kB]
Get:28 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [18.8 kB]
Get:29 http://archive.ubuntu.com/ubuntu xenial-backports/main Sources [3518 B]
Get:30 http://archive.ubuntu.com/ubuntu xenial-backports/universe Sources [6226 B]
Get:31 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [5157 B]
Get:32 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages [8068 B]
Get:33 https://packagecloud.io/github/git-lfs/ubuntu xenial InRelease [23.2 kB]
Get:34 https://packagecloud.io/github/git-lfs/ubuntu xenial/main amd64 Packages [6107 B]
Fetched 27.2 MB in 3s (8332 kB/s)                           
Reading package lists... Done
**fenics@0ca36cf2dd4f:~/local$ sudo apt-get install mercurial**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  javascript-common libjs-excanvas mercurial-common
Suggested packages:
  apache2 | lighttpd | httpd qct kdiff3 | kdiff3-qt | kompare | meld | tkcvs | mgdiff wish
  python-mysqldb python-pygments
The following NEW packages will be installed:
  javascript-common libjs-excanvas mercurial mercurial-common
0 upgraded, 4 newly installed, 0 to remove and 110 not upgraded.
Need to get 1931 kB of archives.
After this operation, 10.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 javascript-common all 11 [6066 B]
Get:2 http://archive.ubuntu.com/ubuntu xenial/universe amd64 libjs-excanvas all 0.r3-4 [45.2 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial/universe amd64 mercurial-common all 3.7.3-1ubuntu1 [1833 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial/universe amd64 mercurial amd64 3.7.3-1ubuntu1 [46.3 kB]
Fetched 1931 kB in 3s (504 kB/s)
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76, <> line 4.)
debconf: falling back to frontend: Readline
Selecting previously unselected package javascript-common.
(Reading database ... 40137 files and directories currently installed.)
Preparing to unpack .../javascript-common_11_all.deb ...
Unpacking javascript-common (11) ...
Selecting previously unselected package libjs-excanvas.
Preparing to unpack .../libjs-excanvas_0.r3-4_all.deb ...
Unpacking libjs-excanvas (0.r3-4) ...
Selecting previously unselected package mercurial-common.
Preparing to unpack .../mercurial-common_3.7.3-1ubuntu1_all.deb ...
Unpacking mercurial-common (3.7.3-1ubuntu1) ...
Selecting previously unselected package mercurial.
Preparing to unpack .../mercurial_3.7.3-1ubuntu1_amd64.deb ...
Unpacking mercurial (3.7.3-1ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up javascript-common (11) ...
Setting up libjs-excanvas (0.r3-4) ...
Setting up mercurial-common (3.7.3-1ubuntu1) ...
Setting up mercurial (3.7.3-1ubuntu1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline

Creating config file /etc/mercurial/hgrc.d/hgext.rc with new version
**fenics@0ca36cf2dd4f:~/local$ hg**
Mercurial Distributed SCM

basic commands:

 add           add the specified files on the next commit
 annotate      show changeset information by line for each file
 clone         make a copy of an existing repository
 commit        commit the specified files or all outstanding changes
 diff          diff repository (or selected files)
 export        dump the header and diffs for one or more changesets
 forget        forget the specified files on the next commit
 init          create a new repository in the given directory
 log           show revision history of entire repository or files
 merge         merge another revision into working directory
 pull          pull changes from the specified source
 push          push changes to the specified destination
 remove        remove the specified files on the next commit
 serve         start stand-alone webserver
 status        show changed files in the working directory
 summary       summarize working directory state
 update        update working directory (or switch revisions)

(use "hg help" for the full list of commands or "hg -v" for details)
fenics@0ca36cf2dd4f:~/local$ hg pull/meg/cbcbeat
hg: unknown command 'pull/meg/cbcbeat'
Mercurial Distributed SCM

basic commands:

 add           add the specified files on the next commit
 annotate      show changeset information by line for each file
 clone         make a copy of an existing repository
 commit        commit the specified files or all outstanding changes
 diff          diff repository (or selected files)
 export        dump the header and diffs for one or more changesets
 forget        forget the specified files on the next commit
 init          create a new repository in the given directory
 log           show revision history of entire repository or files
 merge         merge another revision into working directory
 pull          pull changes from the specified source
 push          push changes to the specified destination
 remove        remove the specified files on the next commit
 serve         start stand-alone webserver
 status        show changed files in the working directory
 summary       summarize working directory state
 update        update working directory (or switch revisions)

(use "hg help" for the full list of commands or "hg -v" for details)
**fenics@0ca36cf2dd4f:~/local$ cd ..**
**fenics@0ca36cf2dd4f:~$ ls**
WELCOME  demo  fenics.env.conf  local  shared
**fenics@0ca36cf2dd4f:~$ cd local**
**fenics@0ca36cf2dd4f:~/local$ ls
fenics@0ca36cf2dd4f:~/local$ cd ..
fenics@0ca36cf2dd4f:~$ cd ..
fenics@0ca36cf2dd4f:/home$ ls**
fenics
**fenics@0ca36cf2dd4f:/home$ cd ..
fenics@0ca36cf2dd4f:/$ ls**
bd_build  boot  etc   lib    media  opt   root  sbin  sys  usr
bin       dev   home  lib64  mnt    proc  run   srv   tmp  var
**fenics@0ca36cf2dd4f:/$ cd home
fenics@0ca36cf2dd4f:/home$ cd ..
fenics@0ca36cf2dd4f:/$ cd local**
bash: cd: local: No such file or directory
**fenics@0ca36cf2dd4f:/$ cd home
fenics@0ca36cf2dd4f:/home$ cd local**
bash: cd: local: No such file or directory
**fenics@0ca36cf2dd4f:/home$ cd ..
fenics@0ca36cf2dd4f:/$ cd ..
fenics@0ca36cf2dd4f:/$ cd home
fenics@0ca36cf2dd4f:/home$ ls**
fenics
**fenics@0ca36cf2dd4f:/home$ cd fenics
fenics@0ca36cf2dd4f:~$ cd local
fenics@0ca36cf2dd4f:~/local$ hg clone https://ErikaSimula@bitbucket.org/meg/cbcbeat**
destination directory: cbcbeat
applying clone bundle from https://api.media.atlassian.com/file/cc792462-04bc-43c3-9f82-a9f1c3b86fea/binary?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiIwMTQyMGZkMS1iZmQ2LTQ3MjAtYmE5My0zY2FiODgyYjUxMTAiLCJhY2Nlc3MiOnsidXJuOmZpbGVzdG9yZTpmaWxlOmNjNzkyNDYyLTA0YmMtNDNjMy05ZjgyLWE5ZjFjM2I4NmZlYSI6WyJyZWFkIl19LCJuYmYiOjE1MjgzODAwMDQsImV4cCI6MTUyODM4MDQyNH0.SpoTYpyCQm-bYErK6ii7eMjy3_8wIH5AAw5iWA8rBJY&client=01420fd1-bfd6-4720-ba93-3cab882b5110
adding changesets
adding manifests
adding file changes
added 726 changesets with 1558 changes to 383 files (+1 heads)                                                                                                                              
finished applying clone bundle
searching for changes
adding changesets
adding manifests
adding file changes
added 23 changesets with 58 changes to 42 files (+3 heads)
updating to branch default
117 files updated, 0 files merged, 0 files removed, 0 files unresolved
**fenics@0ca36cf2dd4f:~/local$ ls**
cbcbeat
**fenics@0ca36cf2dd4f:~/local$ cd cbcbeat
fenics@0ca36cf2dd4f:~/local/cbcbeat$ cd test
fenics@0ca36cf2dd4f:~/local/cbcbeat/test$ py.test -m "fast" -v**
=================================================================================== test session starts ====================================================================================
platform linux2 -- Python 2.7.12, pytest-2.8.7, py-1.4.31, pluggy-0.3.1 -- /usr/bin/python
cachedir: ../.cache
rootdir: /home/fenics/local/cbcbeat, inifile: 
collected 422 items 

unit/test_bidomainsolvers_adjoint.py::TestBidomainSolversAdjoint::test_replay[BasicBidomainSolver-direct-1e-15] FAILED
unit/test_bidomainsolvers_adjoint.py::TestBidomainSolversAdjoint::test_replay[BasicBidomainSolver-iterative-1e-15] FAILED
unit/test_bidomainsolvers_adjoint.py::TestBidomainSolversAdjoint::test_replay[BidomainSolver-direct-1e-15] FAILED
unit/test_bidomainsolvers_adjoint.py::TestBidomainSolversAdjoint::test_replay[BidomainSolver-iterative-1e-10] FAILED
unit/test_merger.py::TestMerger::test_basic_and_optimised_splitting_solver_merge[SplittingSolver] PASSED
unit/test_merger.py::TestMerger::test_basic_and_optimised_splitting_solver_merge[BasicSplittingSolver] PASSED
unit/test_pdesolvers.py::TestBasicBidomainSolver::test_basic_solve PASSED
unit/test_pdesolvers.py::TestBasicBidomainSolver::test_compare_solve_step PASSED
unit/test_pdesolvers.py::TestBasicMonodomainSolver::test_basic_solve PASSED
unit/test_pdesolvers.py::TestBasicMonodomainSolver::test_compare_solve_step PASSED
unit/test_pdesolvers.py::TestBidomainSolver::test_solve PASSED
unit/test_pdesolvers.py::TestBidomainSolver::test_compare_with_basic_solve PASSED
unit/test_pdesolvers.py::TestBidomainSolver::test_compare_direct_iterative PASSED
unit/test_pdesolvers.py::TestMonodomainSolver::test_solve PASSED
unit/test_pdesolvers.py::TestMonodomainSolver::test_compare_with_basic_solve PASSED
unit/test_pdesolvers.py::TestMonodomainSolver::test_compare_direct_iterative PASSED
unit/test_splitting_with_domains.py::test_solver_with_domains PASSED

========================================================================================= FAILURES =========================================================================================
_________________________________________________________ TestBidomainSolversAdjoint.test_replay[BasicBidomainSolver-direct-1e-15] _________________________________________________________

self = <test_bidomainsolvers_adjoint.TestBidomainSolversAdjoint object at 0x7f15740c8c90>, Solver = <class 'cbcbeat.bidomainsolver.BasicBidomainSolver'>, solver_type = 'direct'
tol = 1e-15

   @adjoint
    @fast
    @parametrize(("Solver", "solver_type", "tol"), [
        (BasicBidomainSolver, "direct", 1e-15),
        (BasicBidomainSolver, "iterative", 1e-15),
        (BidomainSolver, "direct", 1e-15),
        (BidomainSolver, "iterative", 1e-10),  # NOTE: The replay is not exact because
            # dolfin-adjoint's overloaded Krylov method is not constent with DOLFIN's
            # (it orthogonalizes the rhs vector as an additional step)
        ])
    def test_replay(self, Solver, solver_type, tol):
        "Test that replay of basic bidomain solver reports success."
    
  self._setup_solver(Solver, solver_type)
        self._solve()
    
   # Check replay
   info_green("Running replay basic (%s)" % solver_type)
>      success = replay_dolfin(stop=True, tol=tol)
E       NameError: global name 'replay_dolfin' is not defined

unit/test_bidomainsolvers_adjoint.py:105: NameError
---------------------------------------------------------------------------------- Captured stdout setup -----------------------------------------------------------------------------------
Calling DOLFIN just-in-time (JIT) compiler, this may take some time.
Calling DOLFIN just-in-time (JIT) compiler, this may take some time.
---------------------------------------------------------------------------------- Captured stderr setup -----------------------------------------------------------------------------------
--- Instant: compiling ---
--- Instant: compiling ---
----------------------------------------------------------------------------------- Captured stdout call -----------------------------------------------------------------------------------
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Running forward basic model
Solving on t = (0, 0.1)
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Solving linear variational problem.
Solving on t = (0.1, 0.2)
Solving linear variational problem.
Solving on t = (0.2, 0.3)
Solving linear variational problem.
Solving on t = (0.3, 0.4)
Solving linear variational problem.
Solving on t = (0.4, 0.5)
Solving linear variational problem.
_______________________________________________________ TestBidomainSolversAdjoint.test_replay[BasicBidomainSolver-iterative-1e-15] ________________________________________________________

self = <test_bidomainsolvers_adjoint.TestBidomainSolversAdjoint object at 0x7f1573dcb890>, Solver = <class 'cbcbeat.bidomainsolver.BasicBidomainSolver'>, solver_type = 'iterative'
tol = 1e-15

   @adjoint
    @fast
    @parametrize(("Solver", "solver_type", "tol"), [
        (BasicBidomainSolver, "direct", 1e-15),
        (BasicBidomainSolver, "iterative", 1e-15),
        (BidomainSolver, "direct", 1e-15),
        (BidomainSolver, "iterative", 1e-10),  # NOTE: The replay is not exact because
            # dolfin-adjoint's overloaded Krylov method is not constent with DOLFIN's
            # (it orthogonalizes the rhs vector as an additional step)
        ])
    def test_replay(self, Solver, solver_type, tol):
        "Test that replay of basic bidomain solver reports success."
    
   self._setup_solver(Solver, solver_type)
        self._solve()
    
   # Check replay
   info_green("Running replay basic (%s)" % solver_type)
>       success = replay_dolfin(stop=True, tol=tol)
E       NameError: global name 'replay_dolfin' is not defined

unit/test_bidomainsolvers_adjoint.py:105: NameError
----------------------------------------------------------------------------------- Captured stdout call -----------------------------------------------------------------------------------
Running forward basic model
Solving on t = (0, 0.1)
Solving linear variational problem.
Solving on t = (0.1, 0.2)
Solving linear variational problem.
Solving on t = (0.2, 0.3)
Solving linear variational problem.
Solving on t = (0.3, 0.4)
Solving linear variational problem.
Solving on t = (0.4, 0.5)
Solving linear variational problem.
___________________________________________________________ TestBidomainSolversAdjoint.test_replay[BidomainSolver-direct-1e-15] ____________________________________________________________

self = <test_bidomainsolvers_adjoint.TestBidomainSolversAdjoint object at 0x7f1573dc6e10>, Solver = <class 'cbcbeat.bidomainsolver.BidomainSolver'>, solver_type = 'direct', tol = 1e-15

    @adjoint
    @fast
    @parametrize(("Solver", "solver_type", "tol"), [
        (BasicBidomainSolver, "direct", 1e-15),
        (BasicBidomainSolver, "iterative", 1e-15),
        (BidomainSolver, "direct", 1e-15),
        (BidomainSolver, "iterative", 1e-10),  # NOTE: The replay is not exact because
            # dolfin-adjoint's overloaded Krylov method is not constent with DOLFIN's
            # (it orthogonalizes the rhs vector as an additional step)
        ])
    def test_replay(self, Solver, solver_type, tol):
        "Test that replay of basic bidomain solver reports success."
    
        self._setup_solver(Solver, solver_type)
        self._solve()
    
        # Check replay
        info_green("Running replay basic (%s)" % solver_type)
>       success = replay_dolfin(stop=True, tol=tol)
E       NameError: global name 'replay_dolfin' is not defined

unit/test_bidomainsolvers_adjoint.py:105: NameError
----------------------------------------------------------------------------------- Captured stdout call -----------------------------------------------------------------------------------
*** Warning: 'enable_adjoint' is set to True, but no dolfin_adjoint installed.
Running forward basic model
Solving on t = (0, 0.1)
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Solving on t = (0.1, 0.2)
Solving on t = (0.2, 0.3)
Solving on t = (0.3, 0.4)
Solving on t = (0.4, 0.5)
__________________________________________________________ TestBidomainSolversAdjoint.test_replay[BidomainSolver-iterative-1e-10] __________________________________________________________

self = <test_bidomainsolvers_adjoint.TestBidomainSolversAdjoint object at 0x7f1573dcb8d0>, Solver = <class 'cbcbeat.bidomainsolver.BidomainSolver'>, solver_type = 'iterative', tol = 1e-10

    @adjoint
    @fast
    @parametrize(("Solver", "solver_type", "tol"), [
        (BasicBidomainSolver, "direct", 1e-15),
        (BasicBidomainSolver, "iterative", 1e-15),
        (BidomainSolver, "direct", 1e-15),
        (BidomainSolver, "iterative", 1e-10),  # NOTE: The replay is not exact because
            # dolfin-adjoint's overloaded Krylov method is not constent with DOLFIN's
            # (it orthogonalizes the rhs vector as an additional step)
        ])
    def test_replay(self, Solver, solver_type, tol):
        "Test that replay of basic bidomain solver reports success."
    
        self._setup_solver(Solver, solver_type)
        self._solve()
    
        # Check replay
        info_green("Running replay basic (%s)" % solver_type)
>       success = replay_dolfin(stop=True, tol=tol)
E       NameError: global name 'replay_dolfin' is not defined

unit/test_bidomainsolvers_adjoint.py:105: NameError
----------------------------------------------------------------------------------- Captured stdout call -----------------------------------------------------------------------------------
Calling FFC just-in-time (JIT) compiler, this may take some time.
*** Warning: 'enable_adjoint' is set to True, but no dolfin_adjoint installed.
Running forward basic model
Solving on t = (0, 0.1)
Calling FFC just-in-time (JIT) compiler, this may take some time.
Calling FFC just-in-time (JIT) compiler, this may take some time.
Solving on t = (0.1, 0.2)
Solving on t = (0.2, 0.3)
Solving on t = (0.3, 0.4)
Solving on t = (0.4, 0.5)
=========================================================================== 405 tests deselected by "-m 'fast'" ============================================================================
=================================================================== 4 failed, 13 passed, 405 deselected in 70.82 seconds ===================================================================
****fenics@0ca36cf2dd4f:~/local/cbcbeat/test$ **



