# CyberSoftwareEngineeringGuidelines
Guidelines for developing software and reverse engineering

The following is a list of guidelines that I try to follow when developing software to make projects more sustainable in the long term. 
Ideally, following the guidelines will prevent major structural issues later on.

These are guidelines, not rules, and as such some of them are expected to be violated at some point, though doing so comes with major downsides.

## You should not commit binaries to source control
- most source control is not optimized for binaries, so every time you commit a new version of the same binary to source control, the size of the repo increases by the size of the binary
- committing binaries to source control causes the amount of time it takes to pull your repo to increase. this slows things down for devs and for CI/CD
- binaries committed to source control can be abused to try to stealthily introduce backdoors, as was the case with the xz_utils backdoor

### if you do choose to commit binaries
- use something like `git-lfs`, which optimizes storage
- avoid committing different versions of the same binary

