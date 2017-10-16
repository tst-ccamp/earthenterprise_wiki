Address sanitizer is a helpful tool built into gcc that detects memory errors such as buffer overflows and memory leaks.  However, it is somewhat tricky to use with Open GEE due to the scons build system.  Instructions for building Open GEE with address sanitizer are given below.

1. Edit earth_enterprise/src/SConstruct and find the if statement around line 165 that sets `linkflags` and `optflags` for the different build types.  Find the statements that correspond to your build type and set the flags as follows (you can also specify `-Og` for `optflags` to partially optimize the code):

        linkflags = ['-fsanitize=address']
        optflags = ['-g', '-fsanitize=address']
1. The build will fail unless you tell address sanitizer that it should not exit when a leak is found via an environment variable.  Scons does not use the environment variables from the shell it is run in, so this must be done directly in scons.  In the same SConstruct file, add the line `env['ENV']['ASAN_OPTIONS'] = 'halt_on_error=0;detect_leaks=0'` at some point after the `env` variable is created (around line 436).  You can remove `;detect_leaks=0'` to allow scons to detect memory leaks.
1. Build and run Open GEE.  Address sanitizer will print out information about any memory problems it finds.  This step works best if you run the fusion command line utitilities rather than the fusion UI.