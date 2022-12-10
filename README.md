# 实训题目

LLVM 编译器的初步学习

# 课题简介

LLVM 是一个著名的开源编译器项目、库、工具，本课题从
LLVM 源代码编译与安装起步，继而从"Hello world!"起步
逐步学习基于 LLVM 的软件编写。

# 目标要求

1. LLVM 源代码编译与安装;
2. 基于 LLVM 的开发入门.

# 初步目标

## 1.LLVM 源代码编译安装

工作环境:Windows

方便个人操作,但使用方面可能较为繁琐
工具:
1. git 2.38.1.windows.1
    - 用于下载llvm源码
2. getgnuwin32 0.6.3
    - 用于在Windows上实现Linux指令
3. Cmake 3.25.0
    - 通过源码编译生成搭建工作环境的项目
4. Microsoft Visual Studio 2022
    - 生成工作环境
5. python 3.10.0
    - 用于自动化测试,搭建过程中未使用

搭建过程
1. 上述工具下载/安装完成
2. 使用getgnuwin32中的download.bat脚本进行各种包的下载
    - 存在源不可用以及文件名因网页选项而被修改等问题,基本选择master或者其他快速的下载源,若文件名出现@viasf=1之类的直接修改文件名即可。
    - 若是使用各种源脚本都加载不了的话直接手动上浏览器自行下载。
3. 使用getgnuwin32中的install.bat脚本进行各种包的安装,之后将安装出现的文件夹中的bin目录放入环境变量,检查一些指令即可。
4. 在下载下来的llvm-project中新建build文件夹,打开[Developer PowerShell for VS 2022](#),将当前目录改为build文件夹后执行以下命令行进行源码编译
```cmake
cmake -G "Visual Studio 17 2022" -Thost="x86"  -DCMAKE_BUILD_TYPE=RELEASE -DLLVM_TARGETS_TO_BUILD="X86" -DLLVM_ENABLE_PROJECTS="clang"  -DLLVM_OPTIMIZED_TABLEGEN=ON ../llvm
```
其中命令行各项为

5. 等待生成项目之后用VS打开LLVM.sln,选择生成模式和类型
    - **模式推荐release,debug过于耗费空间,第一次没经验生成70G还没成功**
    - 此过程极其耗费时间和cpu,其他进程能关就关吧

6. 生成结束后将build文件夹中的Release/bin加入到环境变量,命令行测试clang和llvm-as等工具**先--version查看版本即可**

7. 尝试


## 2.LLVM 的开发入门

思路任意，但实现的东西需要指定
