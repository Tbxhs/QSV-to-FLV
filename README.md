# QSV-to-FLV
QSV转码成FLV的工具

本项目基于：
https://github.com/btnkij/qsv2flv
原项目是C#语言，本项目是C++复刻版。

非常感谢原作者提供的思路，目前网络上能找到的很多QSV2FLV工具都存在转码后时间轴错乱的问题，但原作者的算法能够完美实现转换。  

要编译本项目，必须使用小端模式的CPU（PC平台通常都是小端），建议使用VS2017或更高版本版本的VS，并应该关闭SDL检查，然后将语言标准设置为C++17。  
当然，本项目没有使用任何系统相关的代码，所以完全可以在其它编译器或系统上编译，项目比较简单，这里不单独提供makefile。  


比起原项目，本项目除了改变了语言以外，还做出了一些调整或优化：  
1.为了让编译更简单，只提供控制台版本的程序，通过命令行参数或手动输入完成转码，需要GUI版本可自行封装    
2.去掉原来的代码中的比较重复的部分  
3.大幅度优化IO，提升效率，简单测试发现，C++版的转码速度在C#的版的10倍左右  

本项目理论上已经足够优化，如果还想继续优化，可以考虑以下几个方面入手：  
1.调整算法  
2.增加程序中的IO缓冲区的大小  
3.针对较小的文件，直接把临时数据存放于内存，而不再先写入临时文件再重新读取  
