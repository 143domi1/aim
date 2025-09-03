# aim
**Aim** is built to be a **linux** package manager for the app format **Appimage**.
## How to install?
To install Aim on your linux system follow these instructions.
### Requirments
To install AIM on your system, you need to have python3 preinstalled.
To install python follow these steps: https://www.geeksforgeeks.org/python/how-to-install-python-on-linux/
<br>
Then after you have installed python3 on your system follow these instructions:
## Instructions
### User level install
Download the aim file from the github repo and then place it in the **~/.local/bin/** directory on your system and make it executable 
with this command:
<br>
`chmod +x ~/.local/bin/aim`
### Global level install
Download the aim file from the github repo and then use this command to move the **aim** file
<br>
`sudo mv aim /usr/local/bin/`
<br>
and make it executable with this command:
<br>
`chmod +x /usr/local/bin/aim`

## How to upgrade Aim
Currently **AIM** only supports upgrading it self with this command:
<br>
`aim upgrade`
<br>
## **Note**
<br>
If your AIM file is corrupt or you changed something
<br>

`aim upgrade`
<br>
will overwrite the file with the latest version

## How to Install Apps?
To install apps via **AIM** , you need to type in 
<br>
`aim install {whateverappyouwant}`
### Note:
If the app’s name contains multiple words, make sure to put it in double quotes.
<br>
`aim install "Visual Studio Code"`

## How to Delete apps
To delete apps installed with **AIM**, you need to type in:
<br>
`aim delete {whateverappyouwantodelete.AppImage}`
