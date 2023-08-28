# Development Environments

```` {figure} https://weblog.west-wind.com/images/2015Windows-Live-Writer/Windows-10-Update-1Editing-Environment-V_C883/Path%20Editing_thumb.png
````

## Setup

The most critical step in learning to write any programming language is having a working editor or IDE (integrated development environment.) The following steps will be used to install and set up an editor / IDE for you. First, you will need to decide which operating system you will be working on, then we can get the appropriate software, drivers, and set up a path environment, if need be.

## CLion Academic Account Setup & CLion Installation

<iframe width="560" height="315" src="https://www.youtube.com/embed/4em8Lhnu890" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## WindowsOS

### CLion for WindowOS

<iframe width="560" height="315" src="https://www.youtube.com/embed/pGdDt_Kw76A" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card}

Install CLion
: You can download the latest version of CLion from the official website and install it on your Windows machine.

Install MinGW
: MinGW is a collection of GNU compilers for Windows that includes g++. You can download the installer from the official website and follow the instructions to install it on your Windows machine.

Add MinGW to the PATH environment variable
: After installing MinGW, you need to add its $bin$ directory to the $PATH$ environment variable. To do this, open the $System\ Properties$ dialog box, click on the <kbd>Advanced</kbd> tab, and then click on the <kbd>Environment Variables</kbd> button. In the System Variables section, scroll down and find the Path variable. Click on <kbd>Edit</kbd>, then click on New and add the path to the bin folder of your MinGW installation (e.g., $C:\MinGW\bin$). Click <kbd>OK</kbd> to close all the dialogs.

Configure the CMake toolchain in CLion
: In CLion, go to <kbd>File</kbd> -> <kdb>Settings</kbd> -> <kdb>Build, Execution, Deployment</kbd> -> <kdb>Toolchains</kbd>. Click on the <kdb>+</kbd> icon to add a new toolchain. Choose MinGW as the compiler type and provide the path to the MinGW installation directory (e.g., $C:\MinGW$) as the CMake executable path. Click <kbd>OK</kbd> to save the toolchain.

Create a new C++ project
: In CLion, go to <kbd>File</kbd> -> <kbd>New</kbd> Project. Choose C++ as the project type and select the toolchain you just created. Give your project a name and choose a location to save it.

Write and run your code
: Once you've created your project, you can start writing your code in the main.cpp file. To run your code, click on the Run button in the top toolbar or use the <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>F10</kbd> shortcut.
```

### Visual Studio Code for WindowsOS

``````` {card}
**Setting up Visual Studio Code on Windows OS using the g++ compiler. Here are the steps:**

Install Visual Studio Code  
: You can download the latest version of Visual Studio Code from the official website and install it on your Windows machine.

Install MinGW  
: MinGW is a collection of GNU compilers for Windows that includes g++. You can download the installer from the official website and follow the instructions to install it on your Windows machine.

Add MinGW to the PATH environment variable  
: After installing MinGW, you need to add its bin directory to the PATH environment variable. To do this, open the System Properties dialog box, click on the Advanced tab, and then click on the Environment Variables button. In the System Variables section, scroll down and find the Path variable. Click on Edit, then click on New and add the path to the bin folder of your MinGW installation (e.g., C:\MinGW\bin). Click OK to close all the dialogs.

Install the C/C++ extension in Visual Studio Code  
: In Visual Studio Code, click on the Extensions icon on the left sidebar and search for "C/C++". Click on the Install button to install the extension.

Configure the C++ extension in Visual Studio Code  
: After installing the C/C++ extension, you need to configure it to use the g++ compiler. To do this, open the Command Palette by pressing Ctrl+Shift+P (or F1) and search for "C/C++: Edit Configurations (JSON)". Select this option to open the c_cpp_properties.json file. In this file, add the following lines to the "configurations" array:

``` json
{
    "name": "Win32",
    "includePath": [
        "${workspaceFolder}/**"
    ],
    "defines": [
        "_DEBUG",
        "UNICODE",
        "_UNICODE"
    ],
    "compilerPath": "C:/MinGW/bin/g++.exe",
    "cStandard": "c11",
    "cppStandard": "c++17"
}
```

Make sure to replace the "compilerPath" value with the path to your g++ compiler.

Create a new C++ project  
: In Visual Studio Code, go to File -> New Folder and create a new folder for your project. Open this folder in Visual Studio Code by selecting "Open Folder" from the File menu. Once the folder is open, create a new file called "main.cpp" and start writing your code.

Build and run your code  
: To build your code, open the Command Palette and search for "C/C++: Build and Debug Active File". Select this option to compile your code and generate an executable file. To run your code, open the terminal in Visual Studio Code and navigate to the folder where your executable file was generated. Type the name of the executable file and press Enter to run it.

```````

## Mac OS

### CLion for MacOS

``````` {card}
**Setting up CLion on macOS using the g++ compiler, follow these steps:**

- Download and install CLion from the JetBrains website.
- Install Xcode and its Command Line Tools from the App Store or the Apple Developer website. This will include the g++ compiler.
- Open CLion and create a new project.
- In the "New Project" dialog, select "C++ Executable" and give your project a name.
- In the "Build Type" dropdown, select "Debug" or "Release" depending on your needs.
- Under "C++ Compiler," select "Apple Clang" from the dropdown. This is because Xcode includes the Clang compiler, which is the default C++ compiler on macOS.
- Under "C++ Standard," select the version of the C++ standard you want to use for your project.
- Under "C++ Compiler," click the gear icon next to "Compiler executable" and select "Custom."
- In the "Custom compiler executable" dialog, enter the path to the g++ compiler. The path should be /usr/bin/g++.
- Click "OK" to close the dialog and save the changes.
- CLion should now be set up to use the g++ compiler on macOS. You can write and compile C++ code using CLion as you would with any other IDE.

```````

### Visual Studio Code for MacOS

``````` {card} 
**Setting up Visual Studio Code on macOS using the g++ compiler. Here are the steps:**

Install Xcode Command Line Tools
: Xcode Command Line Tools include the g++ compiler. To install it, open Terminal on your macOS machine and enter the following command:

``` bash
xcode-select --install
```

Install Homebrew
: Homebrew is a package manager for macOS that makes it easy to install and manage software packages. To install Homebrew, enter the following command in Terminal:

``` bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install g++ using Homebrew
: After installing Homebrew, you can use it to install g++. To do this, enter the following command in Terminal:

``` bash
brew install gcc
```

Install the C/C++ extension in Visual Studio Code
: In Visual Studio Code, click on the Extensions icon on the left sidebar and search for "C/C++". Click on the Install button to install the extension.

Configure the C++ extension in Visual Studio Code
: After installing the C/C++ extension, you need to configure it to use the g++ compiler. To do this, open the Command Palette by pressing Command+Shift+P (or F1) and search for "C/C++: Edit Configurations (JSON)". Select this option to open the c_cpp_properties.json file. In this file, add the following lines to the "configurations" array:

``` json
{
    "name": "Mac",
    "includePath": [
        "${workspaceFolder}/**"
    ],
    "defines": [],
    "macFrameworkPath": [
        "/System/Library/Frameworks",
        "/Library/Frameworks"
    ],
    "compilerPath": "/usr/local/bin/g++",
    "cStandard": "c11",
    "cppStandard": "c++17"
}
```

Make sure to replace the "compilerPath" value with the path to your g++ compiler, which should be "/usr/local/bin/g++" if you installed it using Homebrew.

Create a new C++ project
: In Visual Studio Code, go to File -> New Folder and create a new folder for your project. Open this folder in Visual Studio Code by selecting "Open Folder" from the File menu. Once the folder is open, create a new file called "main.cpp" and start writing your code.

Build and run your code
: Open the Command Palette and search for "C/C++: Build and Debug Active File". Select this option to compile your code and generate an executable file. To run your code, open the terminal in Visual Studio Code and navigate to the folder where your executable file was generated. Type the name of the executable file and press Enter to run it.

```````


## Miscellaneous

<iframe width="560" height="315" src="https://www.youtube.com/embed/VhkkDTrbboI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/wY24ehH6mC0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Dm7T8BL7idc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/x8oca0LB6Fc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>