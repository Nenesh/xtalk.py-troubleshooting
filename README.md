# xtalk.py-troubleshooting
Troubleshooting problem and install speech-to-rag xtalk.py
- This is for people that don't know how to get it work and are "noob" (that don't know anything about python).
- More advance user will find other way but this is (I think) the easiest.

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

5°/ Install GIT and GIT-LFS if you don't already have them https://git-scm.com/downloads & https://git-lfs.com/

6°/ Use VScode please. https://code.visualstudio.com/


### How to install:

1. Go to where you want download the git repo. Never use space in the folder name, that cause path problem.
Use "-" or "_" instead of space . (eg: c:/folder/folder name here/ => c:/folder/folder_name_here/).
2. In the search bar on top of the windows
![alt text](https://imgur.com/DR0IY2X.png) 
click on the bar text and type "cmd".
That will open your command prompt directly on this folder.
3. git clone https://github.com/All-About-AI-YouTube/speech-to-rag.git
4. cd speech-to-rag
5. git clone https://huggingface.co/coqui/XTTS-v2
6. On windows, in your folder "speech-to-rag", right click and "Open with Code"
![alt text](https://i.imgur.com/fLSaYP1.png)
If you don't have "Open with code", just open Vscode and drag/drop speech-to-rag in it.
7. In Vscode, open a new terminal (on top, Terminal > Open New Terminal) and type :
conda create -n speechtorag python=3.10
- You can remplace "speechtorag" with whatever name you want for your env name. DON'T USE SPACE.
- python=3.10 is the version of python your environment will be. I highly recommend to use 3.10 because I know it work with this version.
8. conda activate speechtorag
  - If you have change the environment name in conda create, change it here too.
9. pip install -r requirements.txt
10. pip install torch==2.1.2+cu118 torchvision==0.16.2+cu118 torchaudio==2.1.2+cu118 --index-url https://download.pytorch.org/whl/cu118
- That will remplace your toch with a CUDA 11.8 compatible version.

### How to setup:

The xtalk.py script have some problems, the easiest way to fix them is to remplace xtalk.py with the one from this repo.
1. Download the xtalk_fix.py and place it in your speech-to-rag folder
![alt text](https://i.imgur.com/7DFb99l.png)
- I fix the relative path, rework 2 variables to make it easiest to use, add some comment to help you understand the code and delet some unnecessary import.
2. In Vscode, go to the xtalk_fix.py file.
3. In line 21, setup the faster_whisper model (default is "medium" should work fine for 90% of people)
4. In line 25, this is the language of the TTS.
5. In line 26, you can change the speed of the TTS (1.2 is normal speaking speed).
5. In line 27, this is the reference voice (the voice of your TTS).
  - You can change it with whatever voice you want, but the file need to be a 24000Hz or 44100Hz .wav file for best result. (Use audacity to change the format of your file simply).
  - Ones you have the .wav file, just drop it in folder speech-to-rag/XTTS-v2/samples
  - Change the name in the variable (default is audio_file_pth2 = "./XTTS-v2/samples/en_sample.wav", if your file name caroline.wav, then the variable should look like this : audio_file_pth2 = "./XTTS-v2/samples/caroline.wav"

### Now just launch LM Studio Server and run xtalk_fix.py

Edit :  If you get this error : 
RuntimeError: Library cublas64_12.dll is not found or cannot be loaded
![alt text](https://i.imgur.com/ZhJKTlc.png)
- Go to C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.8\bin
- Find cublas64_11.dll
- Make a copy and rename the copy cublas64_12.dll
