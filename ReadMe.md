Hardening.cmake
================

Enables various mitigations. Position Independent Code (enables ASLR and is a prereq for sanitizers), DEP (for Windows), various mitigations against microarchitectural vulnrs that destroy performance ... stuff like this.

How to use
----------

1. Add this repo as a submodule into your repo.
2. Point CMake to search for modules in it.
3. `include(Hardening)`
4. `harden(<your target>)`

clang workaround
-----------------

clang [seems to have a long unfixed bug](https://bugs.llvm.org/show_bug.cgi?id=44594) preventing from using PIC with it.
We workaround it by a bash script. Which itself a heuristics and doesn't work well and is not universal. But at least the resulting binaries pass `hardening-check` test on `Position Independent Executable: yes`. **Though it may be not really because clang MSan refuses to work, saying the binary is not PIC.**
