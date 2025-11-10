# CPP_Hello_World_Application_Visual_Studio_Build_Tools_2022
CPP Hello World Application with Visual Studio Build Tools 2022

# Install Visual Studio Build Tools 2022 Open PowerShell as admin, run: 
# Just adds the installer no content
winget install --id=Microsoft.VisualStudio.2022.BuildTools -e --source winget
# does't work
winget install --force --override "--passive --wait --add Microsoft.VisualStudio.Workload.VCTools;includeRecommended"
# Use this command Adds C/CPP
winget install --id Microsoft.VisualStudio.2022.BuildTools -e --source winget --override "--quiet --wait --norestart --add Microsoft.VisualStudio.Workload.VCTools --includeRecommended --includeOptional"

C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build\vcvarsall.bat

# Include path
C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/include
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Tools\MSVC\14.44.35207\include

# C/C++ bin Path 
C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/bin/Hostx64/x64
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Tools\MSVC\14.44.35207\bin\Hostx86\x64

# Tools path
C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/Common7/Tools
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\Tools

# Need to run the environment 
C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Auxiliary\Build\vcvarsall.bat

Ctrl + Shift + B (runs “Build with VC Build Tools”)

# Documentation on lauch.json
https://code.visualstudio.com/docs/debugtest/debugging#_launch-configurations

# c_cpp_properties.json
{
    "configurations": [
        {
            "name": "Win32",
            "includePath": [
                "${workspaceFolder}/**",
                "C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/include"
            ],
            "defines": [
                "_DEBUG",
                "UNICODE",
                "_UNICODE"
            ],
            "windowsSdkVersion": "10.0.26100.0",
            "compilerPath": "C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/bin/Hostx86/x64/cl.exe",
            "cStandard": "c17",
            "cppStandard": "c++23",
            "intelliSenseMode": "windows-msvc-x64"
        }
    ],
    "version": 4
}

# launch.json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(Windows) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}\\${fileBasenameNoExtension}.exe", // Path to your executable
            "args": [],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "lldb", // Or "gdb" if using MinGW, but for MSVC, typically leave as default or use "lldb" if configured
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "build" // Link to the build task defined in tasks.json
        }
    ]
}

# tasks.json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build",
            "type": "shell",
            "command": "cl.exe",
            "args": [
                "/Zi", // Enable debugging information
                "/EHsc", // Standard exception handling
                "/Fe:", "${fileDirname}\\${fileBasenameNoExtension}.exe", // Output executable name
                "${file}" // Input source file
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "presentation": {
                "reveal": "always"
            },
            "problemMatcher": "$msCompile"
        }
    ]
}

    [vcvarsall.bat] Environment initialized for: 'x64'
    C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools>path
    PATH=C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Tools\MSVC\14.44.35207\bin\HostX64\x64;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\IDE\VC\VCPackages;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\IDE\CommonExtensions\Microsoft\TestWindow;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\MSBuild\Current\bin\Roslyn;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Team Tools\DiagnosticsHub\Collector;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\IDE\Extensions\Microsoft\CodeCoverage.Console;C:\Program Files (x86)\Windows Kits\10\bin\10.0.26100.0\\x64;C:\Program Files (x86)\Windows Kits\10\bin\\x64;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\\MSBuild\Current\Bin\amd64;C:\Windows\Microsoft.NET\Framework64\v4.0.30319;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\IDE\;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\Tools\;C:\WINDOWS\system32;C:\WINDOWS;C:\WINDOWS\System32\Wbem;C:\WINDOWS\System32\WindowsPowerShell\v1.0\;C:\WINDOWS\System32\OpenSSH\;C:\Program Files (x86)\NVIDIA Corporation\PhysX\Common;C:\Users\willi\AppData\Local\nvm;C:\nvm4w\nodejs;C:\Program Files\Git\cmd;C:\Program Files\dotnet\;C:\Program Files\CMake\bin;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\Tools\MSVC\14.44.35207\bin\Hostx86\x64;C:\Users\willi\.pyenv\pyenv-win\bin;C:\Users\willi\.pyenv\pyenv-win\shims;C:\Users\willi\AppData\Local\Microsoft\WindowsApps;C:\Users\willi\AppData\Local\Programs\Microsoft VS Code\bin;C:\Users\willi\AppData\Local\GitHubDesktop\bin;C:\Users\willi\go\bin;C:\Users\willi\AppData\Local\nvm;C:\nvm4w\nodejs;C:\Users\willi\AppData\Local\Programs\Ollama;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\IDE\CommonExtensions\Microsoft\CMake\CMake\bin;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\IDE\CommonExtensions\Microsoft\CMake\Ninja;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\Common7\IDE\VC\Linux\bin\ConnectionManagerExe;C:\Program Files (x86)\Microsoft Visual Studio\2022\BuildTools\VC\vcpkg

    # Prompt
    I want to setup C/C++ on VSCode with Visual Studio Build Tools 2022 for the environment  x64 on latest version of Windows 11. Setup the environment with such configurations as c_cpp_properties.json, launch.json, tasks.json

    project/
│
├── .vscode/
│   ├── c_cpp_properties.json
│   ├── tasks.json
│   └── launch.json
│
├── main.cpp
└── (other source files)

{
  "configurations": [
    {
      "name": "MSVC x64",
      "includePath": [
        "${workspaceFolder}/**",
        "C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/include",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/ucrt",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/shared",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/um",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/winrt"
      ],
      "defines": [
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "windowsSdkVersion": "10.0.26100.0",
      "compilerPath": "C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/bin/Hostx64/x64/cl.exe",
      "cStandard": "c17",
      "cppStandard": "c++20",
      "intelliSenseMode": "msvc-x64"
    }
  ],
  "version": 4
}

{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug (MSVC x64)",
      "type": "cppvsdbg",
      "request": "launch",
      "program": "${workspaceFolder}/${fileBasenameNoExtension}.exe",
      "args": [],
      "stopAtEntry": false,
      "cwd": "${workspaceFolder}",
      "console": "integratedTerminal",
      "preLaunchTask": "Build (MSVC x64)"
    }
  ]
}

{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Build (MSVC x64)",
      "type": "shell",
      "options": {
        "shell": {
          "executable": "C:\\Windows\\System32\\cmd.exe",
          "args": ["/c"]
        }
      },
      "command": "call \"C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\VC\\Auxiliary\\Build\\vcvarsall.bat\" x64 && (taskkill /f /im ${fileBasenameNoExtension}.exe >nul 2>&1 || exit 0) && cl.exe /EHsc /Zi /Od /Fe:\"${workspaceFolder}\\${fileBasenameNoExtension}.exe\" \"${file}\"",
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "problemMatcher": "$msCompile",
      "presentation": {
        "reveal": "always",
        "panel": "shared",
        "clear": true
      }
    }
  ]
}

# Claude
# launch.json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Debug Current File (MSVC x64)",
      "type": "cppvsdbg",
      "request": "launch",
      "program": "${workspaceFolder}/bin/${fileBasenameNoExtension}.exe",
      "args": [],
      "stopAtEntry": false,
      "cwd": "${workspaceFolder}",
      "environment": [],
      "console": "integratedTerminal",
      "preLaunchTask": "Build Debug (MSVC x64)"
    },
    {
      "name": "Debug Multi-File Project (MSVC x64)",
      "type": "cppvsdbg",
      "request": "launch",
      "program": "${workspaceFolder}/bin/${workspaceFolderBasename}.exe",
      "args": [],
      "stopAtEntry": false,
      "cwd": "${workspaceFolder}",
      "environment": [],
      "console": "integratedTerminal",
      "preLaunchTask": "Build Multi-File Debug (MSVC x64)"
    },
    {
      "name": "Run Release Build (MSVC x64)",
      "type": "cppvsdbg",
      "request": "launch",
      "program": "${workspaceFolder}/bin/${fileBasenameNoExtension}.exe",
      "args": [],
      "stopAtEntry": false,
      "cwd": "${workspaceFolder}",
      "environment": [],
      "console": "integratedTerminal",
      "preLaunchTask": "Build Release (MSVC x64)"
    }
  ]
}

# tasks.json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Build Debug (MSVC x64)",
      "type": "shell",
      "options": {
        "shell": {
          "executable": "C:\\Windows\\System32\\cmd.exe",
          "args": ["/c"]
        }
      },
      "command": "call \"C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\VC\\Auxiliary\\Build\\vcvarsall.bat\" x64 && (taskkill /f /im ${fileBasenameNoExtension}.exe >nul 2>&1 || exit 0) && cl.exe /std:c++20 /W4 /nologo /EHsc /Zi /Od /D_DEBUG /DUNICODE /D_UNICODE /Fe:\"${workspaceFolder}\\bin\\${fileBasenameNoExtension}.exe\" \"${file}\"",
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "problemMatcher": "$msCompile",
      "presentation": {
        "reveal": "always",
        "panel": "shared",
        "clear": true
      },
      "detail": "Compile current file with debug flags (C++20, x64)"
    },
    {
      "label": "Build Release (MSVC x64)",
      "type": "shell",
      "options": {
        "shell": {
          "executable": "C:\\Windows\\System32\\cmd.exe",
          "args": ["/c"]
        }
      },
      "command": "call \"C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\VC\\Auxiliary\\Build\\vcvarsall.bat\" x64 && (taskkill /f /im ${fileBasenameNoExtension}.exe >nul 2>&1 || exit 0) && cl.exe /std:c++20 /W4 /nologo /EHsc /O2 /Oi /DNDEBUG /DUNICODE /D_UNICODE /Fe:\"${workspaceFolder}\\bin\\${fileBasenameNoExtension}.exe\" \"${file}\"",
      "group": "build",
      "problemMatcher": "$msCompile",
      "presentation": {
        "reveal": "always",
        "panel": "shared",
        "clear": true
      },
      "detail": "Compile current file with optimization flags (C++20, x64)"
    },
    {
      "label": "Build Multi-File Debug (MSVC x64)",
      "type": "shell",
      "options": {
        "shell": {
          "executable": "C:\\Windows\\System32\\cmd.exe",
          "args": ["/c"]
        }
      },
      "command": "call \"C:\\Program Files (x86)\\Microsoft Visual Studio\\2022\\BuildTools\\VC\\Auxiliary\\Build\\vcvarsall.bat\" x64 && (taskkill /f /im ${workspaceFolderBasename}.exe >nul 2>&1 || exit 0) && cl.exe /std:c++20 /W4 /nologo /EHsc /Zi /Od /D_DEBUG /DUNICODE /D_UNICODE ${workspaceFolder}\\*.cpp /Fe:\"${workspaceFolder}\\bin\\${workspaceFolderBasename}.exe\"",
      "group": "build",
      "problemMatcher": "$msCompile",
      "presentation": {
        "reveal": "always",
        "panel": "shared",
        "clear": true
      },
      "detail": "Compile all .cpp files in workspace root with debug flags"
    },
    {
      "label": "Clean Build Artifacts",
      "type": "shell",
      "options": {
        "shell": {
          "executable": "C:\\Windows\\System32\\cmd.exe",
          "args": ["/c"]
        }
      },
      "command": "(if exist \"${workspaceFolder}\\bin\" rmdir /s /q \"${workspaceFolder}\\bin\") && (del /q \"${workspaceFolder}\\*.obj\" 2>nul || exit 0) && (del /q \"${workspaceFolder}\\*.pdb\" 2>nul || exit 0) && (del /q \"${workspaceFolder}\\*.ilk\" 2>nul || exit 0) && echo Build artifacts cleaned.",
      "problemMatcher": [],
      "presentation": {
        "reveal": "always",
        "panel": "shared",
        "clear": true
      },
      "detail": "Remove all compiled executables and intermediate files"
    }
  ]
}

# c_cpp_properties.json
{
  "configurations": [
    {
      "name": "MSVC x64",
      "includePath": [
        "${workspaceFolder}/**",
        "C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/include",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/ucrt",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/shared",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/um",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/winrt",
        "C:/Program Files (x86)/Windows Kits/10/Include/10.0.26100.0/cppwinrt"
      ],
      "defines": [
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
      ],
      "windowsSdkVersion": "10.0.26100.0",
      "compilerPath": "C:/Program Files (x86)/Microsoft Visual Studio/2022/BuildTools/VC/Tools/MSVC/14.44.35207/bin/Hostx64/x64/cl.exe",
      "cStandard": "c17",
      "cppStandard": "c++20",
      "intelliSenseMode": "msvc-x64"
    }
  ],
  "version": 4
}

# Microsoft
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