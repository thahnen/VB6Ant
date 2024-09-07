# VB6Ant

"Build system" for Visual Basic 6 (Classic) that brings the development process of legacy
applications to the mordern era. Based on Apache Ant as the declarative build tool and the uniform
"Visual Basic 6 (Classic) project structure".

## Visual Basic 6 (Classic) project structure

This uniform directory structure is used to keep all the projects the same and have a better user
experience when working on it directly and with this "build system". The structure is as follows:

```
\                           -> includes the project definition, a README.md and Git-related files
\build\                     -> containing all the build artifact, excluded from Git
\scripts\build.xml          -> the actual Ant build script, generated from this library intially
\scripts\VB6Ant\VB6Ant.xml  -> this very library, currently not supporting Git submodules
\src\
  Classes\                  -> contains Class Modules ("*.cls")
  Controls\                 -> contains User Controls ("*.ctl")
  Forms\                    -> contains Forms ("*.frm" and their resources "*.frx")
  Modules\                  -> contains Modules ("*.bas")
  Resources\                -> contains project related resources like icons or other assets
```

## Ant "commands" usable from the library

The library itself does not only provide tasks to be used by Ant projects linked to Visual Basic 6
but also some "commands" that can be used in order to interact with those projects.

### Create project structure

To create the project structure from scratch or re-create files/folders after deleting them, run
the following command:

```shell
ant -buildfile VB6Ant.xml "vb6.project.create"
  -DbaseDir=C:\Users\thahn\source\repos -DprojectName=TestProject
```

It uses the resources located in the *templates* directory to create the structure of the new
project. It is intended to work with Git out of the box.

### Update Ant library

In order to update the Ant library that is copied to each project, run the following command:

```shell
ant -buildfile VB6Ant.xml "vb6.project.update"
  -DprojectDir=C:\Users\thahn\source\repos\TestProject
```

### Onboard SonarCloud

In order to onboard the project to SonarCloud with all the necessary properties, run the following
command:

```shell
ant -buildfile VB6Ant.xml "vb6.project.sonar"
  -DprojectDir=C:\Users\thahn\source\repos\TestProject
  -Dorganization=SonarCloudOrganization
  -Dtoken=SonarCloudToken
```
