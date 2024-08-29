![labelimg](readme/images/labelimg.png)

Label Studio is a modern, multi-modal data annotation tool
(此labelImg标图软件，相对于官方版本，修改了Readme说明和构建exe的部分。)
=======

LabelImg, the popular image annotation tool created by Tzutalin with the help of dozens contributors, is no longer actively being developed and has become part of the Label Studio community. Check out [Label Studio](https://github.com/heartexlabs/label-studio), the most flexible open source data labeling tool for images, text, hypertext, audio, video and time-series data. [Install](https://labelstud.io/guide/install.html) Label Studio and join the [slack community](https://label-studio.slack.com/) to get started.

![Label Studio](readme/images/label-studio-1-6-player-screenshot.png)

About LabelImg
========

![PyPI version](https://img.shields.io/pypi/v/labelimg.svg)
![GitHub Workflow Status](https://img.shields.io/github/workflow/status/tzutalin/labelImg/Package?style=for-the-badge)
![English](https://img.shields.io/badge/lang-en-blue.svg)
![Chinese](https://img.shields.io/badge/lang-zh-green.svg)
![Japanese](https://img.shields.io/badge/lang-jp-green.svg)

LabelImg is a graphical image annotation tool.

It is written in Python and uses Qt for its graphical interface.

Annotations are saved as XML files in PASCAL VOC format, the format used by [ImageNet](http://www.image-net.org/). Besides, it also supports YOLO and CreateML formats.

![Demo Image](https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo3.jpg)
![Demo Image](https://raw.githubusercontent.com/tzutalin/labelImg/master/demo/demo.jpg)

[Watch a demo video](https://youtu.be/p0nR2YsCY_U)

## Installation（经过实践可行的操作）
### Windows + Anaconda
Open the Anaconda Prompt and go to the _labelImg_ directory
```bash
conda create -n labelImg python=3.8
conda activate labelImg
conda install pyqt=5
conda install -c anaconda lxml
pyrcc5 -o libs/resources.py resources.qrc

python labelImg.py
```
If you want to package it into a separate EXE file
```bash
conda install pyinstaller
pyinstaller --hidden-import=pyqt5 --hidden-import=lxml -F -n "labelImg" -c labelImg.py -p ./libs -p ./
```
move data *folder* to *dist* folder

if not load predefined_classes.txt successfully, fix labelImg.py:
```bash
# argparser.add_argument("class_file", default=os.path.join(os.path.dirname(__file__), "data", "predefined_classes.txt"), nargs="?")
argparser.add_argument("class_file", default=os.path.join(".", "data", "predefined_classes.txt"), nargs="?")
```