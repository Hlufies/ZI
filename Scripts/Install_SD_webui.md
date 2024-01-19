# 1.环境安装
```
conda create -n Aigc  python=3.10.6 
```
# 2.下载stable-diffusion-webui
国内可能需要手动下载，[链接](https://github.com/AUTOMATIC1111/stable-diffusion-webui.git)
# 3. 安装依赖环境
```bash webui.sh```
## 报错1
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
## 报错2

```
Traceback (most recent call last):
  File "/newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/launch.py", line 48, in <module>
    main()
  File "/newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/launch.py", line 39, in main
    prepare_environment()
  File "/newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/modules/launch_utils.py", line 424, in prepare_environment
    run_pip(f"install -r \"{requirements_file}\"", "requirements")
  File "/newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/modules/launch_utils.py", line 144, in run_pip
    return run(f'"{python}" -m pip {command} --prefer-binary{index_url_line}', desc=f"Installing {desc}", errdesc=f"Couldn't install {desc}", live=live)
  File "/newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/modules/launch_utils.py", line 116, in run
    raise RuntimeError("\n".join(error_bits))
RuntimeError: Couldn't install requirements.
Command: "/newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/venv/bin/python3" -m pip install -r "requirements_versions.txt" --prefer-binary
Error code: 1
stdout: Looking in indexes: http://mirrors.aliyun.com/pypi/simple/
.......
.......
  note: This error originates from a subprocess, and is likely not a problem with pip.
error: metadata-generation-failed

× Encountered error while generating package metadata.
╰─> See above for output.

note: This is an issue with the package mentioned above, not pip.
hint: See above for details.

[notice] A new release of pip available: 22.2.1 -> 23.3.2
[notice] To update, run: pip install --upgrade pip
```
```
1. 安装
pip config set global.index-url http://mirrors.aliyun.com/pypi/simple/ 
2、删除源
pip config unset global.index-url
3、查看现在用的哪个源
pip config list
```

```
清华：https://pypi.tuna.tsinghua.edu.cn/simple/
阿里云：http://mirrors.aliyun.com/pypi/simple/
中国科技大学：https://pypi.mirrors.ustc.edu.cn/simple/
华中科技大学：http://pypi.hustunique.com/simple/
上海交通大学：https://mirror.sjtu.edu.cn/pypi/web/simple/
豆瓣：http://pypi.douban.com/simple/
```

## 报错3 
```
安装Clip失败
```
```
使用Clash for linux
```
## 报错3
```
No module 'xformers'. Proceeding without it.
```
```
在webui-user.sh 添加以下代码（Linux系统下）:
export COMMANDLINE_ARGS="--xformers"
```
# 安装结束

<img width="660" alt="image" src="https://github.com/Hlufies/AIGC/assets/130231524/9bfa4844-64ba-4b10-8f92-a082c009d44f">


```
╰─# bash webui.sh  -f --device-id 3

################################################################
Install script for stable-diffusion + Web UI
Tested on Debian 11 (Bullseye), Fedora 34+ and openSUSE Leap 15.4 or newer.
################################################################

################################################################
Running on root user
################################################################

################################################################
python venv already activate or run without venv: /newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/venv
################################################################

################################################################
Launching launch.py...
################################################################
Cannot locate TCMalloc (improves CPU memory usage)
Python 3.10.6 (main, Oct 24 2022, 16:07:47) [GCC 11.2.0]
Version: v1.7.0
Commit hash: cf2772fab0af5573da775e7437e6acdca424f26e
Launching Web UI with arguments: -f --device-id 3 --xformers
Style database not found: /newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/styles.csv
Loading weights [1a189f0be6] from /newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/models/Stable-diffusion/1.5/v1-5-pruned.safetensors
Running on local URL:  http://127.0.0.1:7861

To create a public link, set `share=True` in `launch()`.
Creating model from config: /newdata/gluo/AIGC/stable-diffusion-webui/stable-diffusion-webui/configs/v1-inference.yaml
Startup time: 10.9s (prepare environment: 1.8s, import torch: 3.2s, import gradio: 1.2s, setup paths: 1.5s, initialize shared: 0.1s, other imports: 0.7s, setup codeformer: 0.3s, load scripts: 0.7s, create ui: 0.5s, gradio launch: 0.7s).
Applying attention optimization: xformers... done.
Model loaded in 4.5s (load weights from disk: 1.1s, create model: 0.6s, apply weights to model: 2.1s, calculate empty prompt: 0.6s).
```
