#DOL配置
* ##Description——DOL 框架描述
The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

* ##How to install——DOL 安装笔记
#####1.安装必要的环境*（最重要的一步！）*
更新：
$ sudo apt-get update
安装：
$ sudo apt-get install ant
$ sudo apt-get install openjdk-7-jdk
$ sudo apt-get install unzip
#####2.解压下载文件
新建dol的文件夹：
$ mkdir dol
将dolethz.zip解压到dol文件夹中：
$ unzip dol_ethz.zip -d dol
解压systemc：
$ tar -zxvf systemc-2.3.1.tgz
#####3.编译systemc
解压后进入systemc-2.3.1的目录下：
$ cd systemc-2.3.1
新建一个临时文件夹objdir：
$ mkdir objdir
进入该文件夹objdir：
$ cd objdir
运行configure：
$ ../configure CXX=g++--disable-async-updates
编译：
$ sudo make install
记录路径备用：
$ pwd（得到路径）
#####4.编译dol
修改build_zip.xml文件：
*<property name="systemc.inc" value="（上面已记录的路径）/include"/>*
*<property name="systemc.lib" value="（上面已记录的路径）/lib-linux/libsystemc.a"/>*
最后就可以编译了：
$ ant -f build_zip.xml all
#####5.测试第一个例子
进入build/bin/mian路径下：
$ cd build/bin/main
然后运行第一个例子：
$ ant -f runexample.xml -Dnumber=1
结果如图：
![res.jpg](http://upload-images.jianshu.io/upload_images/3261819-53fa1435d28df086.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- ##Experimental experience——实验感想、实验心得
感想就是，千万记得先配置好环境！因为我的Ubuntu是之前就有的，我就以为环境什么的都是有的了，没想到做到后面发现有各种问题和实验指导不同，找了很久没找到原因，那时才发现是因为没配置好环境。
然后还有，第一次用markdown感觉还行，不算方便也不算难，没得控制字体缩进等格式有些不舒服就是了。
