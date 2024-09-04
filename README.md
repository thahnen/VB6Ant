# VB6Ant

Visual Basic 6 (Classic) for Ant

## VB6Ant.xml

Ant library containing necessary macros and targets to invoke the VB6.EXE (Visual Basic 6 IDE /
compiler) from Ant.

## templates

Directory containing template for generating new projects.

## Ant "commands" usable from the library

The library itself does not only provide tasks to be used by Ant projects linked to Visual Basic 6
but also some "commands" that can be used in order to interact with those projects.

### Create project structure

To create the project structure from scratch or re-create files/folders after deleting them, run
the following command:

```shell
ant -buildfile VB6Ant.xml "vb6.project.create" -DbaseDir=C:\Users\thahn\source\repos -DprojectName=TestProject
```

### Update Ant library

In order to update the Ant library that is copied to each project, run the following comman:

```shell
ant -buildfile VB6Ant.xml "vb6.project.update" -DprojectDir=C:\Users\thahn\source\repos\TestProject
```
