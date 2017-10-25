# Introduction
This document outlines the steps needed to setup QT creator as an integrated development environment (IDE) to build, debug, and maintain OpenGEE source code.

It should be noted that this is purely for purposes of setting up an IDE, as current versions of QT creator do not support QT 3.

# Prerequisites
* QT Creator: http://www.qt.io/download
* OpenGee Source: https://github.com/google/earthenterprise.git

# Setting Up Build Configurations
After starting QT creator, create a new project via **New Project → Import Project → Import Existing Project**

[[/images/ImportExistingProject.png|Import Earth Enterprise]]

Click on **Choose...**. Choose a project name (e.g. **EarthEnterprise**) and then select the **earth_enterprise** folder (which contains most of the source code), then click **Next**.

[[/images/ProjectNameAndLocation.png|Location of earth_enterprise]]

Select the **src** folder

[[/images/Src.png|Select Source Folder]]

Click **Next** then **don't add** the project to any version control.

[[/images/NoVCS.png|Don't add to version control]]

Click **Finish**. This will create 4 files:
1. <ProjectName>.config
2. <ProjectName>.creator
3. <ProjectName>.files
4. <ProjectName>.includes

These files are QT-specific and pertain to the configuration of the project.

# Setup Debug Build Configuration
On the left panel, click on **Projects**, then click the **Add** dropdown box, and then **Build**. For ease of use, this build can be called **Debug**. Click **ok**.

[[/images/NewDebugConfig.png|Debug configuration]]

Under **Build Steps**, click **Add Build Step → Custom Build Step**. Here, custom build steps will be created which will build OpenGEE binaries, run unit tests, and build the installers. For reference about those steps see GitHub OpenGEE [build](https://github.com/google/earthenterprise/blob/master/earth_enterprise/BUILD.md) and [installers](https://github.com/google/earthenterprise/wiki/Install-Fusion-or-Earth-Server) references.

In the **Command** box, put the path to scons (e.g. _/usr/bin/scons_)

In the **Arguments** box, put _-j4 internal=1 build_

Then, click **Add Build Step → Custom Process Step** to create the build step that runs the unit tests and then add another to create the installers.

In the **Command** box, put the path to perl (e.g. _/usr/bin/perl_)

In the **Arguments** box, put _RunAllTests.pl_

In the **Working Directory**, put _%{buildDir}/src/NATIVE-DBG-x86\_64/bin/tests_.

Finally, create one additional step for doing a stage install, in the same manner as before.

In the **Command** box, put the same path to scons.

In the **Argument** box, put _j4 internal=1 stage\_install_.

[[/images/CustomBuildSteps.png|custom build steps]]

Note: to avoid the error **No rule to Make target 'all'. Stop.**, make sure that the **Make: make all** build step is disabled (it is created by default). This is done by clicking on the circle with the line through it or by simply deleting the step altogether.

[[/images/NoMakeAll.png|disable make all step]]

An optional step is to create a **Clean Custom Process Step** using the **Command** _/usr/bin/scons_ and the **Arguments** _-j4 -c internal=1 build_. Also, you may delete the **NATIVE-DBG-x86_64** folder to make absolutely certain that no files are left behind from a previous build. This is done by running the following command from the terminal:  __rm -rf earth_enterprise/src/NATIVE-DBG-x86_64_.

[[/images/CleanStep.png|optional clean step]]

Once done with creating all appropriate steps, perform a build. This is done by **Ctrl-B** or **Build → Build Project <ProjectName>**. If all the prerequisites are present, the build process should start, unit tests executed, and then installers built.

_Note: Sometimes, the unit test build step can fail but succeed when re-run_

[[/images/BuildOutput.png|build output]]

# Debugging and Stepping Into Code

First run the installers to install ‘Fusion’ and ‘Server’, then make sure to start the needed services:
 
_$ sudo service gefusion start_
_$ sudo service geserver start_
 
To start an application using QT Creator and debug it directly, add that application to the project as follow. For example to start and debug ‘Fusion’:
 
On left panel click **Projects**, then click **Run** and add the parameters for your app to debug.

[[/images/DebugSettings.png|Debug settings]]

Once this done, go back to QT Creator menu, then **Debug → Start Debugging** (or **F5**). This would build OpenGEE and start ‘Fusion’ in debug mode.
Debug breakpoints can be inserted into the code to break the execution at the appropriate code lines.

[[/images/StartDebugging.png|start debugging]]

Alternatively you can start any app outside from the IDE (fusion, server, any of the tools) and go back to the **IDE Debug → Attach to running application**.

# Setup Release Build Configuration

Click **Add → Clone Selected** to clone the debug configuration. Call the new configuration **Release**.

[[/images/CloneConfig.png|clone debug configuration]]

The same values can be kept as in the **Debug** configuration with the following exceptions:
* in the scons commands, _internal=1_ should be changed to _release=1_
* any step referencing the _NATIVE-DBG-x86\_64_ folder, should be switched to reference the _NATIVE-REL-x86\_64_ folder

[[/images/ReleaseOptions.png|release configuration options]]
