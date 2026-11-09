# CUTEkit

CUTEkit turns a fresh VPS into a full terminal workstation that its owner can reach from anywhere and easily maintain.

## Language

**Workstation**:
The finished, ready-to-use terminal environment on the VPS: the shell, tools and access setup that CUTEkit produces.
_Avoid_: workbench, workspace, environment

**Server**:
The machine CUTEkit is installed on and that the workstation runs on: a VPS, VM or single-board computer such as a Pi.
_Avoid_: box, host, machine (say "VPS" only in marketing copy)

## Tools

**Tool**:
Any entry in the config, whatever installs it.
_Avoid_: app, package (except in "system package")

**System package**:
A tool installed by apt because the operating system, a service, a login shell, or every user on the server depends on it, or because it is part of a dependency chain.
_Avoid_: system tool, apt tool

**User tool**:
A tool installed by mise: a runtime, CLI, or upstream tool the user works with directly, whose version can differ per project.
_Avoid_: dev tool, mise tool, managed tool

**Custom install**:
A tool that neither apt nor mise can handle, installed by its own script or manual steps.
_Avoid_: curl tool, manual tool
