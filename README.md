# Cross-Compile-ARM
Cross-Compile C/C++ applications for ARM by using Linux and Eclipse

In this article, I'll explain how to cross-compile C/C++ code for Arm based PandaBoard-ES. I'll also mention about Eclipse environment setup.

While making this, I've read the instructions at http://www.lvr.com/eclipse1.htm and imitated them to PandaBoard-ES.

## Requirements :

### Host Machine :
- Ubuntu 12.04 Desktop (It may be used via VMware or VirtualBox)
- Ethernet Connection

## 1) Install Toolchain:

I'll use Sourcery CodeBench Lite Edition for ARM GNU/Linux
- Download the toolchain :
http://www.mentor.com/embedded-software/sourcery-tools/sourcery-codebench/editions/lite-edition/arm-gnu-linux

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/1.png)

### Hint:
You will need to register to download the item.
I've downloaded and worked with Sourcery CodeBench Lite 2013.05-24

- Download tar file
- Extract it to /home/username/

`host# sudo tar -xjvf path/to/tar/file`

## 2) Install Eclipse

`host# sudo apt-get install eclipse`

## 3) Install CDT Add-ons

Open Eclipse
Help > Install New Software..
Enter "http://download.eclipse.org/tools/cdt/releases/kepler" to Work With: area and search
Download all CDT features

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/2.png)

### Hint:
  - C/C++ Development Tools is enough to develop simple C/C++ applications but more features is never bad :)

### Possible Errors:
  - You may not be able to load all of the addons in one shot. Try installing CDT Main Features first, then the other addons.

## 4) Create a C/C++ Project

Right click to the Navigator or Project Explorer View and click New > C++ Project

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/3.png)

Write project name
Select Empty Project
Select Linux GCC
Click Finish

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/4.png)

## 5) Configure for Cross-Compile

Right Click to project > Properties > C/C++ Build > Settings
Click Manage Configurations...
Click New..
Write a new name and copy configuration from Debug or Release.
Click OK
Set your new configuration as Active

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/5.png)

-Under Tool Settings > GCC C++ Compiler
Write /home/db/CodeSourcery/Sourcery_CodeBench_Lite_for_ARM_GNU_Linux/bin/arm-none-linux-gnueabi-g++ as Command.

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/6.png)

-Go to Includes tab under GCC C++ Compiler
Add /home/db/CodeSourcery/Sourcery_CodeBench_Lite_for_ARM_GNU_Linux/arm-none-linux-gnueabi/include/c++/4.7.3 as include folder

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/7.png)

-Go to GCC C++ Linker Tab
Write /home/db/CodeSourcery/Sourcery_CodeBench_Lite_for_ARM_GNU_Linux/bin/arm-none-linux-gnueabi-g++ as Command.

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/8.png)

### Warning!
- You have to change /home/db part to mention your home folder.
- If you installed Toolchain elsewhere, indicate that path.

Apply and close

## 6) Compile the project

Create a source file extended as .cpp

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/9.png)
![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/10.png)

Write a sample code as below and save:
```C
    #include <iostream>
    using namespace std;
    int main() {
     cout <<"Cross Compiled"<<endl;
     return 0;
    }
```
Click the little arrow on build icon. 
Select your cross compile builder.

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/11.png)

Look console and see that build has been finished successfully. You will see something like that.

![alt tag](https://github.com/dBeker/Cross-Compile-ARM/blob/master/Images/12.png)

Your program has been compiled and ready to work with at your pandaboard.
