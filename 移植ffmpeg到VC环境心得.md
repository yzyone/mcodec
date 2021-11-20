
# 移植ffmpeg到VC环境心得 #

  所有想学习ffmpeg的网友有福了，大名鼎鼎的ffmpeg，移植到Windows的VC6版本全部开源，编译环境为VC6+SP5+VCPP5。别忘记了顶贴哦。

移植ffmpeg到windows，主要的修改是ffmpeg中VC6不支持C99语法，简单移植步骤如下:

1：首先装好Linux、VMware和SDL，配置好smb，在Linux下编译通过，验证能正确的Run。

2：把Linux下相应目录的所有文件通过smb拖到Windows，以后的修改移植都在Windows下进行。

3：对照所有同名的.c文件和.o文件，如果有.c文件没有对应的同名.o文件，说明此.c文件没有编译，是多余的，可直接删除。不过我的习惯是在此文件后加.old后缀来标示，这类文件有几十个。注意有几个.c文件是被include在其他.c文件中，因此没有.o文件，不可删除，我的习惯是把这类文件加.inc后缀，并且修改相应include的文件名。这类文件共计有 jpeg_ls.c.inc,mdec.c.inc,motion_est_template.c.inc,svq3.c.inc和wmv2.c.inc。

4：修改config.h文件，关闭掉MMX/SSE2等汇编加速开关。定义CONFIG_WIN32标示目标系统为WIN32。

5：删掉目录下所有Linux编译生成的中间文件，包括.o文件，.d文件，还有Linux下的可执行文件。 如果怕删错了，就做好备份。

6：现在用VC6建一个工程文件，把所有文件的.c和.h文件加入到工程中，不包括ffmpeg.c/ffserver.c文件，不包括改了后缀名的.old文件和.inc文件。

注意在libavcodec和libavformat目录下有些同名的.c文件，为区别同名.c文件，我的习惯是libavcodec目录下的文件名加_codec，libavformat目录下的文件名加_format。

7：为避免思维过多的切换，一次只处理一个方面的内容。首先搜查所有的AVCodec，对照.h文件中的定义改C99语法，通常是填一些NULL或0之类的值，接着搜查并处理所有的AVInputFormat，最后搜查并处理所有的AVOutputFormat。

8：搜查并处理所有AVRational语法。

9：至此，基本上主要的修改已经完成，剩下的主要有 动态数组和一些数组初始化，函数实参初始化等。

10：一维的动态数组比较好改，多维的动态数组比较困难，但是多维的动态数组多半用于编码，如果只要解码可以简单的注释掉。

11：数组初始化和函数实参初始化只需要多加一个临时变量，很简单的修改。

12：有些.h文件在VC6中找不到，有些可以从Linux中拷贝，也可以自己简单定义。最后编译修改.c文件的时候，一个一个的编译，一个一个的修改，没必要全部编译。

最后祝大家好运，移植顺利。开源的ffmpeg 是 51.8.0的版本，我大约修改了5天左右。

https://files.cnblogs.com/mcodec/ffmpeg.51.8_vc6.rar

参考链接：https://www.cnblogs.com/mcodec/articles/1659671.html