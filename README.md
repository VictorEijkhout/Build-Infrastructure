# Build-Infrastructure
Victor's build infrastructure for packages at TACC

## Makefiles

The installation process is driven by makefiles 
which call the configure/cmake and build scripts.
These also contain the current version number and download location.

For a well-behaved package, writing a new makefile is a matter of 
ten minutes.

Repository: https://github.com/VictorEijkhout/Makefiles

## Spec files

Installation in TACC jail is done through spec files.
For each package there is a single spec file, 
which gets customized to each cluster.

Repository: https://github.com/VictorEijkhout/tacc_specfiles

## Testing

Both local installations and official TACC installations can be tested.
Beware: writing the actual tests can be headache.

Repository: https://github.com/VictorEijkhout/software-testing

## Missing from this story

In each cluster's jail there are a few scripts for updating these repositories.
I have not generalized those.

Each cluster has a directory `victor_scripts` in jail.
- Update all repositories: `victor_scripts/pull_all.sh`. 
- Download latest version of the desired package: `victor_scripts/make_download yourpackage`.
  This uses the version from `victor_scripts/makefiles/yourpackage/Makefile`.
- Build:
```
victor_scripts/tacc_specfiles/thiscluster_specfiles/install.sh yourpackage # non-mpi
victor_scripts/tacc_specfiles/thiscluster_specfiles/install.sh -m yourpackage # mpi
victor_scripts/tacc_specfiles/thiscluster_specfiles/install.sh -c g -v 13 yourpackage # one compiler only: g/i/n
victor_scripts/tacc_specfiles/thiscluster_specfiles/install.sh -r yourpackage # only re-install rpms, do not regenerate
victor_scripts/tacc_specfiles/thiscluster_specfiles/install.sh -p yourpackage yourpackage-variant # variant : seq/par or so
```

Notes on the pull script:
- This also installs the cluster-specific `install.sh` packages used above.
- Since jail has git/ssh problems,
  this pull scripts does a `git stash && git pull`. In other words, you can not make permanent changes 
  to the repos from jail.


