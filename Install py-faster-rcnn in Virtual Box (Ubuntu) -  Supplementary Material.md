# Install py-faster-rcnn in Virtual Box (Ubuntu) -  Supplementary Material 
@Dongjie Fan | 1/20/2017

This is a **supplementary material** for caffe installation. I basically followed **@nmonarizqa**'s [instruction](https://github.com/nmonarizqa/mHealth/blob/master/install-py-faster-rcnn-vbox-ubuntu.md) and took some additional steps to solve the problems I met during my own caffe and other parts of py-faster-rcnn (only-CPU mode) installation process.

## **Hardware / Software**

My computer is **ThinkPad L450** with **AMD R5 2GB**. The **Virtual Box** version is  5.1.14 r112924 with **Ubuntu 16.04** installed in it (2GB RAM, 50GB VDI). 



## **Additional Steps for Installation**

**@nmonarizqa**'s [instruction](https://github.com/nmonarizqa/mHealth/blob/master/install-py-faster-rcnn-vbox-ubuntu.md) can basically guide you to install py-faster-rcnn (only-CPU mode) successfully. 

However, I met some other errors when I compiled and tested it. And Following measurements are the soultions to fix those problems.

##### Error 1：

```
Ubuntu 16.04 compilation failure due to "hdf5.h" and similarly "hdf5_hl.h"
```
##### Solution 1：modify the Makefile.config

```
INCLUDE_DIRS := $(PYTHON_INCLUDE) /usr/local/include /usr/include/hdf5/serial/
LIBRARY_DIRS := $(PYTHON_LIB) xcd /usr/local/lib /usr/lib /usr/lib/x86_64-linux-gnu/hdf5/serial/
```



##### Error 2：
```
ImportError: python-tk package
```
##### Solution 2：modify the Makefile.config

Try `sudo apt-get remove python-tk`, then `sudo apt-get clean` so that you will re-download the package, `sudo apt-get install python-tk`, and then try importing again. 



## **Run Demo**

```
cd $FRCN/tools
python demo.py --cpu --net zf
```

 Hopefully, you will see the result like this:

![demo1](https://drive.google.com/open?id=0Bz2f7HxaHOt5bjBvLV9kTml0ejA)

![demo2](https://drive.google.com/open?id=0Bz2f7HxaHOt5dTk2eHp0ZHZ4eG8)



## Reference
- [nmonarizqa's instruction](https://github.com/nmonarizqa/mHealth/blob/master/install-py-faster-rcnn-vbox-ubuntu.md)

- [Ubuntu 15.04 compilation failure due to "hdf5.h" instead of "hdf5/serial/hdf5.h" and similarly "hdf5_hl.h"](https://github.com/BVLC/caffe/issues/2690)

- [Python-tk package not recognized in Python 2.7.3](http://stackoverflow.com/questions/11043844/python-tk-package-not-recognized-in-python-2-7-3)


##### **Other Links**

- [Ubuntu 14.04 VirtualBox VM](https://github.com/BVLC/caffe/wiki/Ubuntu-14.04-VirtualBox-VM)

- [py-faster-rcnn GitHub page](https://github.com/rbgirshick/py-faster-rcnn)

- [Ubuntu 16.04 or 15.10 Installation Guide](https://github.com/BVLC/caffe/wiki/Ubuntu-16.04-or-15.10-Installation-Guide)

- [How to setup py-faster-rcnn with CPU only](https://github.com/rbgirshick/py-faster-rcnn/issues/123)


