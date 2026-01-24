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
  Controls\                 -> contains User Controls ("*.ctl" and their resources "*.ctx")
  Forms\                    -> contains Forms ("*.frm" and their resources "*.frx")
  Modules\                  -> contains Modules ("*.bas")
  Resources\                -> contains project related resources like icons or other assets
```

## Create project structure

To create the project structure from scratch or re-create files/folders after deleting them, run
the following command on this very library from wherever in the file system:

```shell
ant -buildfile VB6Ant.xml "vb6.project.create"
  -DbaseDir=C:\Users\thahn\source\repos -DprojectName=TestProject
```

It uses the templated `build.xml` located in the *templates* directory to create the structure of
the new project.
This library is then added as a Git Submodule inside the `scripts\VB6Ant` directory.
