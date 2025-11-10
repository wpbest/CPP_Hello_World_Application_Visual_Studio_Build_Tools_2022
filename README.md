# CPP_Hello_World_Application_Visual_Studio_Build_Tools_2022
CPP Hello World Application with Visual Studio Build Tools 2022

# Install Visual Studio Build Tools 2022 Open PowerShell as admin, run: 
# Just adds the installer no content
winget install --id=Microsoft.VisualStudio.2022.BuildTools -e --source winget

# Use this command Adds C/CPP
winget install --id Microsoft.VisualStudio.2022.BuildTools -e --source winget --override "--quiet --wait --norestart --add Microsoft.VisualStudio.Workload.VCTools --includeRecommended --includeOptional"

# Include path
C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/include
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Tools\MSVC\14.44.35207\include

# C/C++ bin Path 
C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/bin/Hostx64/x64
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Tools\MSVC\14.44.35207\bin\Hostx86\x64

# Tools path
C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/Common7/Tools
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\Tools

# Need to run to setop the environment 
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build\vcvarsall.bat

Ctrl + Shift + B (runs “Build with VC Build Tools”)

# Documentation on lauch.json
https://code.visualstudio.com/docs/debugtest/debugging#_launch-configurations



project/
│
├── .vscode/
│   ├── c_cpp_properties.json
│   ├── tasks.json
│   └── launch.json
│
├── main.cpp
└── (other source files)


# Microsoft default configuration which does not work
# tasks.json
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "cppbuild",
			"label": "C/C++: cl.exe build active file",
			"command": "cl.exe",
			"args": [
				"/Zi",
				"/EHsc",
				"/nologo",
				"/Fe${fileDirname}\\${fileBasenameNoExtension}.exe",
				"${file}"
			],
			"options": {
				"cwd": "${fileDirname}"
			},
			"problemMatcher": [
				"$msCompile"
			],
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"detail": "compiler: cl.exe"
		}
	]
}

# launch.json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(Windows) Launch",
            "type": "cppvsdbg",
            "request": "launch",
            "program": "enter program name, for example ${workspaceFolder}/a.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "console": "externalTerminal"
        }

    ]
}