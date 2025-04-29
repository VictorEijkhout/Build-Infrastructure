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

## Testing

Both local installations and official TACC installations can be tested.
Beware: writing the actual tests can be headache.

Repository: https://github.com/VictorEijkhout/software-testing
