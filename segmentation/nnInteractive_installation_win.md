In command line
Default installation pytorch did not work

Remove pixi installation in Terminal admin mode (PowerShell)

Remove pixi
`>Remove-Item -Recurse -Force "$env:USERPROFILE\.pixi"`

remove pixi cache
`Remove-Item -Recurse -Force "$env:LOCALAPPDATA\pixi`

Remove project folders created with pixi
`Remove-Item -Recurse -Force "$env:LOCALAPPDATA\nninteractive-server"`

Install torch 2.7.0 with cuda126 appeared to work
`pip install torch==2.7.0 torchvision==0.22.0 torchaudio==2.7.0 --index-url https://download.pytorch.org/whl/cu126`

Type cmd to install nninteractive server
`pip install nninteractive`

printed out error message:
>ERROR: pip's dependency resolver does not currently take into account all the packages that are installed. This behaviour is the source of the following dependency conflicts.
>torchaudio 2.7.0+cu126 requires torch==2.7.0+cu126, but you have torch 2.6.0 which is incompatible.`

Reinstall torch 2.7.0+cu125 printed out again conflict error about requiring torch 2.6.0

However, nninteractive server shoulde be able detect gpu and successfully started




In conda, I initially installed 2.7.0 with cu126 but reported installed 2.6.0 after installing the nn server.

Afterwards, I installed torch 2.7.0 with cu126 again, it appeared to work. 

nn server needs to be installed in cmd admin mode.

When open first time, open admin mode.

