# 1.环境安装
```
conda create -n Aigc  python=3.10.6 
```
# 2.下载stable-diffusion-webui
国内可能需要手动下载，[链接](https://github.com/AUTOMATIC1111/stable-diffusion-webui.git)
# 3. 安装依赖环境
```bash webui.sh```
## 如果报错
```
################################################################
Install script for stable-diffusion + Web UI
Tested on Debian 11 (Bullseye), Fedora 34+ and openSUSE Leap 15.4 or newer.
################################################################

################################################################
ERROR: This script must not be launched as root, aborting...
################################################################
```
```
解决办法:
bash webui.sh -f   
```
