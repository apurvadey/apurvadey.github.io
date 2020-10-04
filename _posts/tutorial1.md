# How to run a C/C++ Program in VSCode

### Often it happens that we try to run a simple hello world program written in C/C++ in our favourite coding platform VSCode, but it isn't able to. We may see error like: "gcc" is not recognized as an internal or external command, operable program or batch file.

### So to fix this, first of all, we need to be clear that the prequisites for running any c/cpp program are present in our local system. Here is a blog to do the same, step by step.

## Follow the following steps to run a C/C++ Program in VSCode

## Prequisites

1. VSCode Setup
### Most probably, you have got the setup as you are here to solve this issue. If not, you can follow [this link](https://code.visualstudio.com/) for the download and setup of Visual Studio Code.
2. MinGW Setup
### Follow [this link](http://www.mingw.org/wiki/Getting_Started) to get your MinGW setup done.

## Let me give you the highlights for the same. 
1. On downloading the setup exe file, **run it as administrator**. 
2. A dialog box will appear for download and setup of MinGW Installation Manager
3. Click on **install** button in first step.
4. Then, installation directory will show up, with the installation path mentioned which is most likely to be **C:\MinGW**, click on **Continue**.
5. Then a long downloading session would begin, let it happen and click on **continue** when the option is enabled.
6. The **MinGW Installation Manager** is installed and the application would open automatically.
7. You will be redirected to the **basic setup tab**, where you would see a list of packages. You need to install the Package **mingw32-gcc-g++**, right click and select the option **Mark for installation**.
8. Then from the main menu, click on the **Installation** option, and further select **Apply changes**.
9. A dialog box with the title **Schedule of Pending Actions** would appear, there select the **Apply** button and again a long downloading process would begin. Let it happen, give it time. You may Select **close** option manually on completion of download, or you may select the **Close automatically, when activity is complete** radio button for your convenience.
10. After the dialog box closes, the installation is done. 
11. Next, you need to open the **File Explorer** and go the location where MinGW is located (go to the Installation path, refer step 4).
12. Click on MinGW and go to the bin folder where the files like gcc.exe and g++.exe are located. Copy the address of the bin folder.
13. Then right click on **This PC** option that appears in the left sidebar of our File explorer. You may select the **Properties** option. 
14. Then Go to **Advanced System Settings** located in the left sidebar of the **System** dialog box that appears. 
15. Go to the **Advanced** Tab, and select **Environment Variables** option located in the bottommost area. 
16. Under the **User Variables** Panel, click on **Path** option and then click **edit**.
17. Click on **New** option and paste the copied address of the **MinGW bin folder** there. Click **OK** once done.
18. Again click **OK**.
19. To check the gcc installation is successful or not, open the command prompt and write the command 
```
g++ --version
gdb --version
```
The corresponding version would be returned if installation is done.
20. Further write in the command prompt

```
mkdir projects
cd projects
mkdir helloworld
cd helloworld
code .
```


21. You can mold the folder location as per your need. code. command will open the helloworld directory in the VSCode as your working directory.
22. In the File explorer title bar, select **new file** button or press **Ctrl + N** for the same. Create the **helloworld.cpp** file and write the code for the same, proceed with saving it **(Ctrl + S)**.
23. Next, from the main menu, select **Terminal > Configure Default Build task**. In the dropdown, select **g++.exe build active** file. This will create a **tasks.json** file in a .vscode folder and open it. 
24. No changes are required there as such. but ideally, it appears like 


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


25. Now return to your helloworld.cpp file and press **Ctrl+Shift+B** to buiild the tasks mentioned in tasks.json. 
26. In the terminal, the message of the task being execeuted will be displayed. 
27. Click a **new terminal using the + button**, where the helloworld will be the working directory.
28. You can run helloworld by typing **helloworld.exe (or .\helloworld.exe if you use powershell)**.
29. Your code will run!!!!!
30. Congrats.

## Thanks for reading!
