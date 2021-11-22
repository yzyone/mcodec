
# 最新 ffmpeg-0.8 移植到 windows 开源代码 #

最新 ffmpeg-0.8 开源编码解码库，从linux下移植到windows vs2005，全部开源。

需要 Intel C++ Compile 和 开源的SDL库支持，由于 Intel C++ Compile支持C99语法，所以源代码改动很小很小。

 

主要的修改

1：添加了linux中有而windows没有的几个头文件，放在libstapi目录下。

2：在 config.h文件末尾添加一些定义，屏蔽一些linux和windows的差别。

3：设置工程的附加路径 "./libstdapi;../;./"。

4：设置C99语法支持。

5：在三到五个.h文件中添加#include "config.h"。

6：因为gcc和vs2005对if()判断语句的编译差别，导致源码中有一些修改。

7：其 他的修改集中在allcodecs.c和allformats.c文件中。

8：在不同的目录下有相同文件名的.c文件，加 _avcodec,_avformat,_avutil,_swscale等后缀以示区别

 

实际编译时，双击 ffplay.icproj工程文件打开vs2005，然后编译运行。

附带有测试文件CLOCKTXT.avi。

下载地址:https://files.cnblogs.com/mcodec/ffmpeg-0.8.7z

intel c/c++ compiler 下载地址: http://lfiles3.brothersoft.com/development/compilers_and_ides/w_cc_p_10.1.020.exe

intel c/c++ compiler license 下载地址 :https://files.cnblogs.com/mcodec/icc_lic.rar

分类: ffmpeg/ffplay

标签: 最新 ffmpeg-0.8 vs2005 开源