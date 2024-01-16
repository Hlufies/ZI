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
pip config set global.index-url http://mirrors.aliyun.com/pypi/simple/ 
```
