# CyberSoftwareEngineeringGuidelines
Guidelines for developing software and reverse engineering

The following is a list of guidelines that I try to follow when developing software to make projects more sustainable in the long term.
Ideally, following the guidelines will prevent major structural issues later on.

These are guidelines, not rules, and as such some of them are expected to be violated at some point, though doing so comes with major downsides.

## Thou shall use source control to track your source code
- Source control helps to track down when bugs were introduced, keep a record of old good versions of code, etc

## Thou shall not commit binaries to source control
- most source control is not optimized for binaries, so every time you commit a new version of the same binary to source control, the size of the repo increases by the size of the binary
- committing binaries to source control causes the amount of time it takes to pull your repo to increase. this slows things down for devs and for CI/CD
- binaries committed to source control can be abused to try to stealthily introduce backdoors, as was the case with the xz_utils backdoor

### if you do choose to commit binaries
- use something like `git-lfs`, which optimizes storage
- avoid committing different versions of the same binary

## Thou shall not commit build artifacts to source control
- all of the same reasons as not committing binaries to source control, plus you know you will be changing these items frequently.

## Thou shall not push code directly to the main branch on repos that more than one person use

## Thou shall test your code before pushing
- Untested code is frequently broken code.

## Thou shall design code for testability
- Untestable code is code that should be assumed to be riddled with bugs
- If you can't test a component without testing the whole product, you probably need a new test

## Thou shall not break the build on the main branch
- any commits to a repo should not break the build, as it causes issues for devs that pull while the build is broken

## Thou shall automate the build process CI/CD pipelines
- ci/cd ensures that you know if something will break the build as soon as it happens
- automated regression tests help to identify when you have broken some existing functionality

## Thou shall document the build process in in-tree documentation
- this enables new developers to start up with development immediately

## Thou shall enable build reproducibility by documenting build toolchain info, OS, compiler, build dependencies, etc. in in-tree documentation

## Thou shall document as if you will not be present to elaborate or explain later

## Thou shall document the repo pulling process in in-tree documentation
- This is a small and easy thing to do that will help new developers

## Thou shall document the build environment in in-tree documentation

## Thou shall document a tool usage for both users and developers
- Your devs shouldn't have to fight your code to be able to test a bug fix
- Your users should be able to build and use your code without having to read it first

## Thou shall perform code reviews on new code
- see https://github.com/google/eng-practices for examples of good practices

## Thou shall document the core review process

## Thou shall document newly established processes that will need to be reproduced in the future
- If you need to extract symbols or something for a new version of a product, it needs to be documented.

## Thou shall use a ghidra server if more than one person is reversing a file at the same time
- Not doing this just wastes time and effort

## Thou shall strive to limit the size of merge requests so that a merge request does not take more than a maximum of one day to review
- Exceedingly large code reviews waste time and are a little bit discrespectful of your code reviewers' time

## Thou shall respond to merge request comments quickly

## Thou shall create issues or user stories in some sort of tracking system as soon as you are aware that they need to be done
- Tracking issues/user-stories in your head is not reasonable

## Thou shall write code for human readability
- At the end of the day your code needs to be readable, understandable, and modifiable by normal humans

## Thou shall write code defensively; assuming it will be copied and incorrectly used by a future developer

## Thou shall ask questions (within reason)
- If you don't know something and can't google it, ask a question to a dev who knows. Then document it.

## Thou shall comment code explaining what it does (within reason)

## Thou shall include information about reverse engineered structures and where to look to review their usage or re-reverse them in code comments
- If a structure needs to be re-reversed in a different version or if it was so fundamentally incorrect that it needs to be re-reversed from scratch, this will make everyone's lives easier

## Thou shall maintain one and only one main branch per repo in source control
- Multiple main branches probably means you are maintaining duplicate copies of the same source code

## Thou shall tag releases

## Thou shall not fork internally maintained repos unless original code cannot be maintained or the new commits are undesired in the original repo
- Every time you fork a repo you ensure that code has to be committed to two places when fixing a bug in both repos

### before choosing to fork
- ensure that you at least attempt to commit to the existing repo

## Thou shall not maintain multiple copies of the same code

## Thou shall establish and follow coding syntax/style standards

## Thou shall not hard-code file paths or IP addresses
- Both will likely change
