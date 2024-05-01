# xtalk.py-troubleshooting
Troubleshooting problem and install speech-to-rag xtalk.py
This is for people that don't know how to get it work are "noob" (that don't know anything about python).
More advance user will find other way but this is (I think) the easiest.

Before starting :

1°/ Download and install miniconda.
I have too many problem with windows venv, I use miniconda to manager environment stuff, you should do the same.
https://docs.anaconda.com/free/miniconda/index.html

2°/ You need to install ffmpeg.
https://phoenixnap.com/kb/ffmpeg-windows

3°/ You need to install CUDA 11.8 (waaaaaay to many problem with other versions).
This is a Windows 10 link, if you have another system, download for you system.
https://developer.nvidia.com/cuda-11-8-0-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exe_local

4°/ I make it run without problem with Python 3.10. Should work fine with python 3.11 (but not tested). DON'T USE PYTHON 3.12.

5°/ Install GIT if you don't already have it https://git-scm.com/downloads


### How to install:

1. Go to where you want download the git repo. Never use space in the folder name, that cause path problem.
Use "-" or "_" instead of space . (eg: c:/folder/folder name here/ => c:/folder/folder_name_here/).
2. In the search bar on top of the windows
![alt text](https://imgur.com/DR0IY2X.png) 
click on the bar text and type "cmd".
That will open you command prompt directly on this folder.
3. git clone https://github.com/All-About-AI-YouTube/speech-to-rag.git
4. cd speech-to-rag
5. git clone https://huggingface.co/coqui/XTTS-v2
6. conda create -n speechtorag python=3.10
- You can remplace "speechtorag" with whatever name you want for your env name. DON'T USE SPACE.
- python=3.10 is the version of python your environment will be. I highly recommend to use 3.10 because I know it work with this version.
6. conda activate speechtorag
  - If you have change the environment name in conda create, change it here too.
7. pip install -r requirements.txt
8. pip install torch==2.1.2+cu118 torchaudio==2.1.2+cu118 --index-url https://download.pytorch.org/whl/cu118
- That will remplace your toch with a CUDA 11.8 compatible version.

### How to setup:

The xtalk.py script have some problems, the easiest way to fix them is to remplace xtalk.py with the one from this repo.
1. Download th


