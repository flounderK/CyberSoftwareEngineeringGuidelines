# CyberSoftwareEngineeringGuidelines
Guidelines for developing software and reverse engineering

The following is a list of guidelines that I try to follow when developing software to make projects more sustainable in the long term. 
Ideally, following the guidelines will prevent major structural issues later on.

These are guidelines, not rules, and as such some of them are expected to be violated at some point, though doing so comes with major downsides.

## You should use source control to track your source code
- Source control helps to track down when bugs were introduced, keep a record of old good versions of code, etc

## You should not commit binaries to source control
- most source control is not optimized for binaries, so every time you commit a new version of the same binary to source control, the size of the repo increases by the size of the binary
- committing binaries to source control causes the amount of time it takes to pull your repo to increase. this slows things down for devs and for CI/CD
- binaries committed to source control can be abused to try to stealthily introduce backdoors, as was the case with the xz_utils backdoor

### if you do choose to commit binaries
- use something like `git-lfs`, which optimizes storage
- avoid committing different versions of the same binary

## You should not commit build artifacts to source control
- all of the same reasons as not committing binaries to source control, plus you know you will be changing these items frequently. 

## You should not push code directly to the main branch on repos that more than one person use

## You should test your code before pushing

## You should design code for testability

## You should not break the build on the main branch
- any commits to a repo should not break the build

## You should automate the build process CI/CD pipelines 
- ci/cd ensures that you know if something will break the build as soon as it happens
- automated regression tests help to identify when you have broken some existing functionality

## You should document the build process in in-tree documentation
- this enables new developers to start up with development immediately

## You should enable build reproducibility by documenting build toolchain info, OS, compiler, build dependencies, etc. in in-tree documentation

## You should document as if you will not be present to elaborate or explain later

## You should document the repo pulling process in in-tree documentation

## You should document the build environment in in-tree documentation

## You should perform code reviews on new code 
- see https://github.com/google/eng-practices

## You should document the core review process

## You should document newly established processes that will need to be reproduced in the future

## You should use a ghidra server if more than one person is reversing a file at the same time

## You should strive to limit the size of merge requests so that a merge request does not take more than a maximum of one day to review

## You should respond to merge request comments quickly

## You should create issues or user stories in some sort of tracking system as soon as you are aware that they need to be done

## You should write code for human readability

## You should write code defensively; assuming it will be copied and incorrectly used by a future developer

## You should ask questions (within reason)

## You should comment code explaining what it does (within reason)

## You should include information about reverse engineered structures and where to look to review their usage or re-reverse them in code comments

## You should maintain one and only one main branch per repo in source control

## You should tag releases

## You should not fork internally maintained repos unless original code cannot be maintained or the new commits are undesired in the original repo
- Every time you fork a repo you ensure that code has to be committed to two places when fixing a bug in both repos

### before choosing to fork
- ensure that you at least attempt to commit to the existing repo

## You should not maintain multiple copies of the same code

## You should establish and follow coding syntax/style standards

## You should not hard-code file paths or IP addresses
