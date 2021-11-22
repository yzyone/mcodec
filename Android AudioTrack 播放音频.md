Android AudioTrack 播放音频

Posted on 2011-01-12 12:25  mcodec  阅读(4980)  评论(1)  编辑  收藏  举报

Android平台播放多媒体数据通常是指定 datasource, 由系统处理剩下的事情。但是当要添加其他不被直接支持的媒体格式并可能要直接控制输出时，指定datasource的方法就不好使了。本例使用AudioTrack类直接在应用层输出解码后的PCM音频数据，于是就可以自由的添加音频解码器，连接AudioTrack输出，扩展支持的媒体格式。本例在1.6版下用模拟器调试通过。

下载地址: https://files.cnblogs.com/mcodec/AuTrack.7z

分类: Android

标签: Android AudioTrack 范例