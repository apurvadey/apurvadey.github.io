---
layout: post
title: "How to run C and C++ Program in VSCode"
date: 2020-10-04
comments: true
categories: 
---



Often it happens that we try to run a simple hello world program written in C/C++ in our favourite coding platform VSCode, but it isn't able to. We may see error like: "gcc" is not recognized as an internal or external command, operable program or batch file.

So to fix this, first of all, we need to be clear that the prequisites for running any c/cpp program are present in our local system. Here is a blog to do the same, step by step.

## Follow the following steps to run a C/C++ Program in VSCode

## Prerequisites

*  **VSCode Setup**

Most probably, you have got the setup as you are here to solve this issue. If not, you can follow [this link](https://code.visualstudio.com/) for the download and setup of Visual Studio Code.


* **MinGW Setup**

Follow [this link](http://www.mingw.org/wiki/Getting_Started) to get your MinGW setup done.

## Let me give you the highlights for the same. 

* On downloading the setup exe file, **run it as administrator**. 

* A dialog box will appear for download and setup of MinGW Installation Manager

* Click on **install** button in first step.

* Then, installation directory will show up, with the installation path mentioned which is most likely to be **C:\MinGW**, click on **Continue**.

* Then a long downloading session would begin, let it happen and click on **continue** when the option is enabled.

* The **MinGW Installation Manager** is installed and the application would open automatically.

* You will be redirected to the **basic setup tab**, where you would see a list of packages. You need to install the Package **mingw32-gcc-g++**, right click and select the option **Mark for installation**.

* Then from the main menu, click on the **Installation** option, and further select **Apply changes**.

* A dialog box with the title **Schedule of Pending Actions** would appear, there select the **Apply** button and again a long downloading process would begin. Let it happen, give it time. You may Select **close** option manually on completion of download, or you may select the **Close automatically, when activity is complete** radio button for your convenience.

* After the dialog box closes, the installation is done. 

* Next, you need to open the **File Explorer** and go the location where MinGW is located (go to the Installation path, refer step 4).

* Click on MinGW and go to the bin folder where the files like gcc.exe and g++.exe are located. Copy the address of the bin folder.

* Then right click on **This PC** option that appears in the left sidebar of our File explorer. You may select the **Properties** option. 

* Then Go to **Advanced System Settings** located in the left sidebar of the **System** dialog box that appears. 

* Go to the **Advanced** Tab, and select **Environment Variables** option located in the bottommost area. 

* Under the **User Variables** Panel, click on **Path** option and then click **edit**.

* Click on **New** option and paste the copied address of the **MinGW bin folder** there. Click **OK** once done.

* Again click **OK**.

* To check the gcc installation is successful or not, open the command prompt and write the command 
```
g++ --version
gdb --version
```
The corresponding version would be returned if installation is done.

* Further write in the command prompt

```
mkdir projects
cd projects
mkdir helloworld
cd helloworld
code .
```

You can mold the folder location as per your need.
code. command will open the helloworld directory in the VSCode as your working directory.

Now, let us do the required configuration in VSCode.

* In the File explorer title bar, select **new file** button or press **Ctrl + N** for the same. Create the **helloworld.cpp** file and write the code for the same, proceed with saving it **(Ctrl + S)**.

* Next, from the main menu, select **Terminal > Configure Default Build task**. In the dropdown, select **g++.exe build active** file. This will create a **tasks.json** file in a .vscode folder and open it. 

* No changes are required there as such. but ideally, it appears like 


```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "type": "shell",
      "label": "C/C++: g++.exe build active file",
      "command": "C:\\Program Files\\mingw-w64\\x86_64-8.1.0-posix-seh-rt_v6-rev0\\mingw64\\bin\\g++.exe",
      "args": ["-g", "${file}", "-o", "${fileDirname}\\${fileBasenameNoExtension}.exe"],
      "options": {
        "cwd": "${workspaceFolder}"
      },
      "problemMatcher": ["$gcc"],
      "group": {
        "kind": "build",
        "isDefault": true
      }
    }
  ]
}
```


* Now return to your helloworld.cpp file and press **Ctrl+Shift+B** to buiild the tasks mentioned in tasks.json. 

* In the terminal, the message of the task being execeuted will be displayed. 

* Click a **new terminal using the + button**, where the helloworld will be the working directory.

* You can run helloworld by typing **helloworld.exe (or .\helloworld.exe if you use powershell)**.

* *Your code will run!!!!!*

* *Congrats.*

## *Thanks for reading!*
