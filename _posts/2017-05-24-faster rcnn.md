---
layout:     post
title:      "faster rcnn配置记录"
subtitle:   "自己数据集训练、测试模型"
date:       2017-05-24
author:     "QiQ"
header-img: "BingWallpaper-2017-05-24.jpg"
tags:
    - caffe
    - faster rcnn
    - Ubuntu
---
## faster rcnn安装
>[python版本faster rcnn github地址](https://github.com/rbgirshick/py-faster-rcnn)  
>[MATLAB版本](https://github.com/ShaoqingRen/faster_rcnn)  

##  在py-faster-rcnn上使用cudnn v5加速库  
py-faster-rcnn工程上，默认使用的是cudnn-v4，如果直接使用cudnn-v5编译faster rcnn里的caffe会报以下错误：

<pre><code>In file included from ./include/caffe/util/cudnn.hpp:5:0,  
                 from ./include/caffe/util/device_alternate.hpp:40,
                 from ./include/caffe/common.hpp:19,
                 from src/caffe/data_reader.cpp:6:
/usr/local/cuda/include/cudnn.h:799:27: note: declared here
 cudnnStatus_t CUDNNWINAPI cudnnSetPooling2dDescriptor</code></pre>

解决方法：
使用cudnn-v5版本的文件替换faster_rcnn中caffe里面的cudnn文件。因为我机器上有caffe SSD的文件，所以直接从caffe SSD里面copy了相关的cudnn文件进行替换。

```
   cp caffe/inlude/caffe/layers/cudnn_* caffe-fast-rcnn/include/caffe/layers/
   cp caffe/src/caffe/layers/cudnn_* caffe-fast-rcnn/src/caffe/layers/
   cp caffe/include/caffe/util/cudnn.hpp caffe-fast-rcnn/include/caffe/util/
```

修改后编译通过，正常运行。
参考：
>[如何在py-faster-rcnn上使用最新的cudnn v5加速库](http://blog.csdn.net/kexinmcu/article/details/53178428)

## 训练模型

## 测试
训练模型时只有两个类别（背景+person），在运行demo.py使用自己训练的模型检测图片时，还需要修改py-faster-rcnn/models/pascal_voc/VGG16/faster_rcnn_alt_opt文件夹下的faster_rcnn_test.pt文件。根据自己训练的类别修改num_output参数。
```
layer {
  name: "cls_score"
  type: "InnerProduct"
  bottom: "fc7"
  top: "cls_score"
  inner_product_param {
    num_output: 21
  }
}
layer {
  name: "bbox_pred"
  type: "InnerProduct"
  bottom: "fc7"
  top: "bbox_pred"
  inner_product_param {
    num_output: 84
  }
}
```
参考：

>[Faster-RCNN+ZF用自己的数据集训练模型(Python版本)](http://blog.csdn.net/sinat_30071459/article/details/51332084)

>[目标检测--Faster RCNN2](https://saicoco.github.io/object-detection-4/)

>[]()
