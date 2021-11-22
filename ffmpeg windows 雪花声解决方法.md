
# ffmpeg windows 雪花声解决方法 #

替换所有文件里的<math.h>为<mathimf.h>即可。

我用ffmpeg-0.6.3版测试时，好像mathimf.h文件和其他文件有冲突，需要修改源码。

和qdm2.c文件中的 QDM2Complex *complex;声明相冲突，修改为QDM2Complex *complex1；即可。

和g726.c文件中的static int16_t g726_decode(G726Context* c, int I)中的I冲突，修改为I1即可。

修改完变量声明，同时需修改相关代码，改完音频就完美了。

 

mathimf.h文件是intel c compiler自带的头文件。

 

 

分类: ffmpeg/ffplay

标签: ffmpeg windows 雪花声解决方法