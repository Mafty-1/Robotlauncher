# RobotLauncher


一个用于启动 QQ AI机器人的 Windows 一键启动器。


基于：

- NapCatQQ
- OneBot11
- AstrBot


实现：

```
双击启动器

↓

启动NapCat

↓

启动AstrBot

↓

打开WebUI

↓

机器人上线

```


---

# 功能


## 自动启动


支持：

- NapCat启动
- AstrBot启动
- WebUI自动打开


---

## 自动检测


启动前检测：

- NapCat是否已经运行
- AstrBot是否已经运行
- 端口是否占用


避免重复启动。


---

# 环境要求


## Windows


支持：

```
Windows 10
Windows 11
```


## Python


要求：

```
Python 3.10+
```


---

# 文件结构


推荐目录：

```
D:\RobotLauncher


├── start_robot.py

├── RobotLauncher.spec

├── icon.ico

└── README.md

```


---

# 配置修改


打开：

```
start_robot.py
```


---

# 1. 修改AstrBot路径


找到：

```python
ASTRBOT_PATH
```


默认：

```python
ASTRBOT_PATH = r"D:\AstrBot-master\AstrBot-master"
```


修改为你的AstrBot目录。


例如：

```python
ASTRBOT_PATH = r"E:\AstrBot"
```


---

# 2. 修改NapCat路径


找到：

```python
NAPCAT_PATH
```


默认：

```python
NAPCAT_PATH = r"D:\NapCat.Shell.Windows.OneKey"
```


修改为你的NapCat目录。


例如：

```python
NAPCAT_PATH = r"E:\NapCat"
```


---

# 3. 修改NapCat启动文件


默认：

```
launcher-user.bat
```


需要保证：

```
NapCat目录

├── launcher-user.bat

├── NapCatWinBootMain.exe

└── napcat.mjs

```


如果文件名字不同：

修改：

```python
launcher-user.bat
```


---

# WebUI配置


## AstrBot


默认：

```
http://127.0.0.1:6185
```


代码：

```python
ASTRBOT_WEB = "http://127.0.0.1:6185"
```


---

## NapCat


默认：

```
http://127.0.0.1:3000
```


代码：

```python
NAPCAT_WEB = "http://127.0.0.1:3000"
```


---

# 使用方法


## Python运行


进入：

```cmd
cd /d D:\RobotLauncher
```


启动：

```cmd
python start_robot.py
```


---

# 打包EXE


安装：

```cmd
pip install pyinstaller
```


进入目录：

```cmd
cd /d D:\RobotLauncher
```


删除旧文件：

```cmd
rmdir /s /q build

rmdir /s /q dist
```


重新生成：

```cmd
pyinstaller RobotLauncher.spec
```


生成：

```
dist

└── RobotLauncher.exe
```


---

# 启动流程


第一次：

```
启动QQ

↓

启动NapCat

↓

配置OneBot11

↓

启动AstrBot

↓

测试机器人

```


以后：

```
双击RobotLauncher.exe
```


即可。


---

# 常见问题


## AstrBot端口占用


错误：

```
端口6185已被占用
```


解决：

查看：

```cmd
netstat -ano | findstr 6185
```


关闭：

```cmd
taskkill /PID PID号码 /F
```


---

## OneBot连接失败


检查NapCat：

应该出现：

```
WebSocket反向服务:
ws://127.0.0.1:6199/ws
```


AstrBot配置：

```
ws://127.0.0.1:6199/ws
```


---

## NapCat WebUI


地址：

```
http://127.0.0.1:3000
```


如果需要Token：

查看NapCat启动日志：

```
WebUi Token:
xxxxxxxx
```


访问：

```
http://127.0.0.1:3000/webui?token=xxxxxxxx
```


---

# License


MIT License
