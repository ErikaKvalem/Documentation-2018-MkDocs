# Terminal code for cbcbeat installation 

fenics@0ca36cf2dd4f:~/local$ sudo apt-get install mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package mercurial
fenics@0ca36cf2dd4f:~/local$ sudo apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  openssh-server openssh-client

E: Package 'ssh' has no installation candidate
fenics@0ca36cf2dd4f:~/local$ sudo apt-get install openssh-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-client is already the newest version (1:7.2p2-4ubuntu2.2).
openssh-client set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fenics@0ca36cf2dd4f:~/local$ 

fenics@0ca36cf2dd4f:~/local$ ssh
usage: ssh [-1246AaCfGgKkMNnqsTtVvXxYy] [-b bind_address] [-c cipher_spec]
           [-D [bind_address:]port] [-E log_file] [-e escape_char]
           [-F configfile] [-I pkcs11] [-i identity_file] [-L address]
           [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port]
           [-Q query_option] [-R address] [-S ctl_path] [-W host:port]
           [-w local_tun[:remote_tun]] [user@]hostname [command]
fenics@0ca36cf2dd4f:~/local$ sudo apt-get update
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
fenics@0ca36cf2dd4f:~/local$ sudo apt-get install mercurial
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
fenics@0ca36cf2dd4f:~/local$ hg
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
fenics@0ca36cf2dd4f:~/local$ cd ..
fenics@0ca36cf2dd4f:~$ ls
WELCOME  demo  fenics.env.conf  local  shared
fenics@0ca36cf2dd4f:~$ cd local
fenics@0ca36cf2dd4f:~/local$ ls
fenics@0ca36cf2dd4f:~/local$ cd ..
fenics@0ca36cf2dd4f:~$ cd ..
fenics@0ca36cf2dd4f:/home$ ls
fenics
fenics@0ca36cf2dd4f:/home$ cd ..
fenics@0ca36cf2dd4f:/$ ls
bd_build  boot  etc   lib    media  opt   root  sbin  sys  usr
bin       dev   home  lib64  mnt    proc  run   srv   tmp  var
fenics@0ca36cf2dd4f:/$ cd home
fenics@0ca36cf2dd4f:/home$ cd ..
fenics@0ca36cf2dd4f:/$ cd local
bash: cd: local: No such file or directory
fenics@0ca36cf2dd4f:/$ cd home
fenics@0ca36cf2dd4f:/home$ cd local
bash: cd: local: No such file or directory
fenics@0ca36cf2dd4f:/home$ cd ..
fenics@0ca36cf2dd4f:/$ cd ..
fenics@0ca36cf2dd4f:/$ cd home
fenics@0ca36cf2dd4f:/home$ ls
fenics
fenics@0ca36cf2dd4f:/home$ cd fenics
fenics@0ca36cf2dd4f:~$ cd local
fenics@0ca36cf2dd4f:~/local$ hg clone https://ErikaSimula@bitbucket.org/meg/cbcbeat
destination directory: cbcbeat
applying clone bundle from https://api.media.atlassian.com/file/cc792462-04bc-43c3-9f82-a9f1c3b86fea/binary?token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiIwMTQyMGZkMS1iZmQ2LTQ3MjAtYmE5My0zY2FiODgyYjUxMTAiLCJhY2Nlc3MiOnsidXJuOmZpbGVzdG9yZTpmaWxlOmNjNzkyNDYyLTA0YmMtNDNjMy05ZjgyLWE5ZjFjM2I4NmZlYSI6WyJyZWFkIl19LCJuYmYiOjE1MjgzNzY1NDcsImV4cCI6MTUyODM3Njk2N30.-41grfLxAcaJGwqODZyEaEdT-T_uYxf618wr0pwlML8&client=01420fd1-bfd6-4720-ba93-3cab882b5110
adding changesets
adding manifests
adding file changes
files [===================>                                                            ] files [=============files [========================>                                       files [===================>                   files [=============================>                                                            ] 131/383 9m34s

