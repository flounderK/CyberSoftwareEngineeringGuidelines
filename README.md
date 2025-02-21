# CyberSoftwareEngineeringGuidelines
Guidelines for developing software and reverse engineering

The following is a list of guidelines that I try to follow when developing software to make projects more sustainable in the long term. 
Ideally, following the guidelines will prevent major structural issues later on.

These are guidelines, not rules, and as such some of them are expected to be violated at some point, though doing so comes with major downsides.

# You should not commit binaries to source control
- most source control is not optimized for binaries, so every time you commit a new version of the same binary to source control, the size of the repo increases by the size of the binary
- committing binaries to source control causes the amount of time it takes to pull your repo to increase. this slows things down for devs and for CI/CD
- binaries committed to source control can be abused to try to stealthily introduce backdoors, as was the case with the xz_utils backdoor

## if you do choose to commit binaries
- use something like `git-lfs`, which optimizes storage
- avoid committing different versions of the same binary

# You should use source control to track your source code
- Source control helps to track down when bugs were introduced, keep a record of old good versions of code, etc

# You should not commit build artifacts to source control
- all of the same reasons as not committing binaries to source control, plus you know you will be changing these items frequently. 

# You should not fork internally maintained repos
- Every time you fork a repo you ensure that code has to be committed to two places when fixing a bug in both repos

## before choosing to fork
- ensure that you at least attempt to commit to the existing repo

# You should not break the build on the main branch
- any commits to a repo should not break the build

# You should use some sort of CI/CD pipeline for building and testing
- ci/cd ensures that you know if something will break the build as soon as it happens
- automated regression tests help to identify when you have broken some existing functionality

# You should perform code reviews on new code 

# Merge requests should not take more than a maximum of _ to review

# You should create issues or user stories in some sort of tracking system as you become aware of them





