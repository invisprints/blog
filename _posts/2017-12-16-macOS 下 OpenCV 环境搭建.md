---
toc: true
layout: post
description: macOS 下 OpenCV 环境搭建
categories: [others]
title: macOS 下 OpenCV 环境搭建
comments: true
---

# macOS 下 OpenCV 环境搭建
因为专业的原因，需要搭建个图像处理的开发环境。上网研究了下相关资料，再结合符合中国特色社会主义的时代背景，决定在 macOS 下用 Clion 搭建 OpenCV 等图像开发环境。

<!-- more -->

##安装 Clion
Clion 是 JetBrains 公司近几年推出的 C/C++ 跨平台 IDE，由于学生免费使用并且包含 Vim 插件，所以相对于 Xcode 神一般的操作逻辑，我最终选择了 Clion。
有人问为什么不用我最喜欢的 Vim 骚遍全场呢，原因是 Vim 擅长处理小项目和临时打开一些文件，对于这种图像处理之类的大项目，还是用 IDE 来的方便，当然必须要有 Vim 插件！！！
[Clion 官方主页](https://www.jetbrains.com/clion/)
[下载地址](https://www.jetbrains.com/clion/download/)

##安装 OpenCV
对于这种著名的开源的又不知道从何开始安装的鬼东西，我们一律用 HomeBrew 安装，省时省力又简单。

    brew install opencv

安装的 OpenCV 版本应该是 3.3.1 或以后的。

##创建第一个项目
安装好后怎么用呢？其实我也不太会，照着网上的教程一步一步来呗。

1. 用 Clion 创建一个空白项目。
2. 打开 CMakeLists.txt 配置文件，增加如下语句

    ```
    find_package(OpenCV)
    include_directories( ${OpenCV_INCLUDE_DIRS} )
    
    target_link_libraries( Myexe ${OpenCV_LIBS} )
    ```
    
    其中 Myexe 替换成你的可执行文件的名称。
3. 将图片（如 demo.png）拷贝到项目的工作目录下（你也可以不拷贝，但是下面的图片路径就需要你自己指定）。
4. 在 main.cpp 中输入如下代码:

    ```cpp
    #include <iostream>
    #include <opencv2/opencv.hpp>       //调用 OpenCV 的库
    
    using namespace cv;
    
    int main()
    {
        Mat image;      // OpenCV 中图片格式为 Mat
    
        image = imread( "../demo.png"); //读取图片
        if( image.empty() )             //检查是否读取成功
        {
            std::cout <<  "Could not open or find the image" << std::endl ;
            return -1;
        }
        imshow("demo",image);   //显示图片
    
        waitKey();
        return 0;
    }
    ```

5. 运行程序，这下我们的第一个基于 OpenCV 的工程就搭建好了！

##OpenCV 进阶
更多的内容请访问[OpenCV 官网教程](https://docs.opencv.org/master/d9/df8/tutorial_root.html)，教程给得很详细，而且有可以练手的地方，是很好的入门教程。

