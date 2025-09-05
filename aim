#!/usr/bin/env python3
required_packages = ["os", "shutil", "sys", "platform", "subprocess", "requests"]
try:
    import os
    import shutil
    import sys
    import platform
    import subprocess
    import requests
except ImportError:
    print("CRITICAL RUNTIME ERROR 5 - A critical libary is missing, this program requires the critical libary to be installed.\n What do you want to do?\n1.Let AIM download the required libary.\n2.Exit the program.")
    answer  = input("")
    if answer == "1":
        print("Downloading..")
        for package in required_packages:
            subprocess.call(["pip", "install", package])
    elif answer == "2":
        sys.exit(1)


apps = {
    "Auryo" : {
        "url": "https://github.com/sneljo1/auryo/releases/download/v2.5.4/Auryo-2.5.4.AppImage",
        "Verified": "no" 
        },
    "Audacity" :{
        "url": "https://github.com/audacity/audacity/releases/download/Audacity-3.7.5/audacity-linux-3.7.5-x64-22.04.AppImage",
        "Verified": "yes"
    },
    "CPod" :{
        "url": "https://github.com/z-------------/CPod/releases/download/v1.28.2/CPod-1.28.2-x86_64.AppImage",
        "Verified": "yes"
    },
    "Hypnos" :{
        "url": "https://hypnosplayer.org/download/beta6/Hypnos-nix-64bit-beta6_2019-07-14_b1.AppImage",
        "Verified": "yes"
    },
    "Melodie" :{
        "url": "https://github.com/feugy/melodie/releases/download/v2.0.0/melodie-2.0.0-x86_64.AppImage",
        "Verified": "yes"
    },
    "Pathephone" :{
        "url": "https://github.com/pathephone/pathephone-desktop/releases/download/v2.2.1/pathephone-desktop-2.2.1-x86_64.AppImage",
        "Verified": "yes"
    },
    "Poddr" :{
        "url": "https://github.com/Sn8z/Poddr/releases/download/v2.1.0/Poddr-2.1.0.AppImage",
        "Verified": "yes"
    },
    "QXGEdit" :{
        "url": "https://sourceforge.net/projects/qxgedit/files/qxgedit/1.0.1/qxgedit-1.0.1-2.1.x86_64.AppImage/download",
        "Verified": "no"
    },
    "QmidiNet" :{ 
        "url": "https://sourceforge.net/projects/qmidinet/files/qmidinet/1.0.1/qmidinet-1.0.1-2.1.x86_64.AppImage/download",
        "Verified": "no"
    },
    "Sharp Tunes" :{
        "url": "https://github.com/MD-AZMAL/Sharp-Tune/releases/download/v1.0.3/sharp-tune-1.0.3-x86_64.AppImage",
        "Verified": "yes"
    },
    "Sonic Lineup" :{
        "url": "https://code.soundsoftware.ac.uk/attachments/download/2766/SonicLineup-1.1-x86_64.AppImage",
        "Verified": "yes"
    },
    "Sonic Visualiser" :{
        "url": "https://code.soundsoftware.ac.uk/attachments/download/2880/SonicVisualiser-5.2.1-x86_64.AppImage",
        "Verified": "yes"
    },
    "Swag Lyrics" :{
        "url": "https://github.com/srevinsaju/swaglyrics-appimage/releases/download/latest/swaglyrics-x86_64.AppImage",
        "Verified": "no"
    },
    "synthv1" :{
        "url": "https://sourceforge.net/projects/synthv1/files/synthv1/1.3.2/synthv1-jack-1.3.2-9.1.x86_64.AppImage/download",
        "Verified": "yes"
    },
    "Unofficial Sonos Controller for Linux" :{
        "url": "https://github.com/pascalopitz/unoffical-sonos-controller-for-linux/releases/download/v0.4.0-rc1/sonos-controller-unofficial-0.4.0-rc1.AppImage",
        "Verified": "no",
        "arm64": "https://github.com/pascalopitz/unoffical-sonos-controller-for-linux/releases/download/v0.4.0-rc1/sonos-controller-unofficial-0.4.0-rc1-arm64.AppImage",
        "arm32": "https://github.com/pascalopitz/unoffical-sonos-controller-for-linux/releases/download/v0.4.0-rc1/sonos-controller-unofficial-0.4.0-rc1-armv7l.AppImage"
    },
    "Blowfish" :{
        "url": "https://github.com/kremalicious/blowfish/releases/download/v1.6.0/Blowfish-1.6.0.AppImage",
        "Verified": "no"
    },
    "BunqDesktop" :{
        "url": "https://github.com/bunqCommunity/bunqDesktop/releases/download/0.9.10/bunqDesktop-0.9.10-x86_64.AppImage",
        "Verified": "no"
    },
    "CRITERIA1D PRO" :{
        "url": "https://github.com/ARPA-SIMC/CRITERIA1D/releases/download/v1.8.7/CRITERIA1D_PRO-x86_64.AppImage",
        "Verified": "yes"
    },
    "Carpenters" :{
        "url": "https://github.com/uhlibraries-digital/carpenters/releases/download/v2.5.2/carpenters-2.5.2-x86_64.AppImage",
        "Verified": "yes"
    },
    "Elphyre-WalletShell" :{
        "url": "https://github.com/SpookyPool/elphyre-wallet-electron/releases/download/2.0.4/Elphyre-WalletShell-v2.0.4-linux.AppImage",
        "Verified": "yes"
    },
    "ExeQt" :{
        "url": "https://github.com/AlexandruIstrate/ExeQt/releases/download/v1.2.2/ExeQt-v1-2-2-x86_64.AppImage",
        "Verified": "yes"
    },
    "f-crm" :{
        "url": "https://github.com/jgaa/f-crm/releases/download/v0.2.0-beta/f-crm-x86_64-0.2.0.AppImage",
        "Verified": "yes"
    },
    "GitQlient" :{
        "url": "https://github.com/francescmaestre/GitQlient/releases/download/dev-latest/GitQlient-1.6.3-88-g2fb103c1-x86_64.AppImage",
        "Verified": "yes"
    },
    "goldendict" :{
        "url": "https://github.com/Abs62/goldendict/releases/download/continuous/GoldenDict-661dd4d-x86_64.AppImage",
        "Verified": "yes"
    },
    "Gospel Pdf viewer" :{
        "url": "https://github.com/ksharindam/gospel-pdf-viewer/releases/download/v3.2.0/Gospel_PDF-x86_64.AppImage",
        "Verified": "no",
        "arm64": "https://github.com/ksharindam/gospel-pdf-viewer/releases/download/v3.2.0/Gospel_PDF-armhf.AppImage"
    },
    "Munt" :{
        "url": "https://github.com/muntorg/munt-official/releases/download/v3.0.7/Munt-3.0.7-x64.AppImage",
        "Verified": "yes",
        "arm64": "https://github.com/muntorg/munt-official/releases/download/v3.0.7/Munt-lite-3.0.7-arm64.AppImage"
    },
    "Blender" :{
        "url": "https://github.com/Lethja/blender-appimage/releases/download/2025-08-21/blender-4.5.2-x86_64.AppImage.zip",
        "Verified": "no"
    },
    "Blender LTS" :{
        "url": "https://github.com/Lethja/blender-appimage/releases/download/2025-08-21/blender-4.2.13-x86_64.AppImage.zip",
        "Verified" : "no"
    },
    "Gimp" :{
        "url": "https://download.gimp.org/gimp/v3.0/linux/GIMP-3.0.4-x86_64.AppImage",
        "Verified": "yes",
        "arm64": "https://download.gimp.org/gimp/v3.0/linux/GIMP-3.0.4-aarch64.AppImage"
    },
    "Gimp Development Edition" :{
        "url": "https://download.gimp.org/gimp/v3.1/linux/GIMP-3.1.4-x86_64.AppImage",
        "Verified": "yes",
        "arm64": "https://download.gimp.org/gimp/v3.1/linux/GIMP-3.1.4-x86_64.AppImage"
    },
    "Krita" :{
        "url": "https://download.kde.org/stable/krita/5.2.11/krita-5.2.11-x86_64.AppImage",
        "Verified": "yes"
    },
    "Krita Plus Nightly" :{
        "url": "https://cdn.kde.org/ci-builds/graphics/krita/krita-5.2/linux/krita-5.2.13-prealpha-4f376aba8d-x86_64.AppImage",
        "Verified": "yes"
    },
    "Firefox" :{
        "url": "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox/firefox-142.0.r20250827004350-x86_64.AppImage",
        "Verified": "no"
    },
    "Firefox Beta" :{
        "url": "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-beta/firefox-beta-143.0.r20250901090535-x86_64.AppImage",
        "Verified": "no"
    },
    "Firefox Nightly" :{
        "url": "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-nightly/firefox-nightly-144.0.r20250902094807-x86_64.AppImage",
        "Verified" : "no"
    },
    "Firefox ESR" :{
        "url": "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-esr-next/firefox-esr-next-102.3.r20220912135840-x86_64.AppImage",
        "Verifed": "no"
    },
    "Firefox Developer Edition" :{
        "url": "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-devedition/firefox-devedition-143.0.r20250901090535-x86_64.AppImage",
        "Verifed": "no"
    },
    "Google Chrome" :{
        "url": "https://github.com/ivan-hc/Chrome-appimage/releases/download/continuous/Google-Chrome-stable-140.0.7339.80-1-x86_64.AppImage",
        "Verified": "no"
    },
    "Google Chrome Beta" :{
        "url": "https://github.com/ivan-hc/Chrome-appimage/releases/download/continuous/Google-Chrome-beta-141.0.7390.7-1-x86_64.AppImage",
        "Verified": "no"
    },
    "Google Chrome Unstable" :{
        "url": "https://github.com/ivan-hc/Chrome-appimage/releases/download/continuous/Google-Chrome-unstable-141.0.7378.3-1-x86_64.AppImage",
        "Verified": "no"
    },
    "Brave Nightly" :{
        "url": "https://github.com/srevinsaju/Brave-AppImage/releases/download/v1.84.31/Brave-nightly-v1.84.31-x86_64.AppImage",
        "Verified": "no"
    },
    "Brave Beta" :{
        "url": "https://github.com/srevinsaju/Brave-AppImage/releases/download/v1.83.90/Brave-beta-v1.83.90-x86_64.AppImage",
        "Verified": "no"
    },
    "Brave" :{
        "url": "https://github.com/srevinsaju/Brave-AppImage/releases/download/v1.82.159/Brave-stable-v1.82.159-x86_64.AppImage",
        "Verified": "no"
    },
    "htop" :{
        "url": "https://github.com/henry-hsieh/htop.appimage/releases/download/v3.3.0/Htop-x86_64.AppImage",
        "Verified": "no"
    },
    "Visual Studio Code" :{
        "url": "https://github.com/valicm/VSCode-AppImage/releases/download/latest/VSCode-x86_64.AppImage",
        "Verified": "yes"
    },
    "Zen" :{
        "url": "https://github.com/zen-browser/desktop/releases/download/1.15.2b/zen-x86_64.AppImage",
        "Verified": "yes",
        "arm64": "https://github.com/zen-browser/desktop/releases/download/1.15.2b/zen-aarch64.AppImage"
    },
    "LibreWolf" :{
        "url": "https://gitlab.com/api/v4/projects/24386000/packages/generic/librewolf/142.0.1-1/LibreWolf.x86_64.AppImage",
        "Verified": "yes",
        "arm64": "https://gitlab.com/api/v4/projects/24386000/packages/generic/librewolf/142.0.1-1/LibreWolf.aarch64.AppImage"
    },
    "Floorp" :{
        "url": "https://github.com/Portable-Linux-Apps/floorp-AppImage/releases/download/v12.1.3%402025-09-01_1756743432/Floorp-v12.1.3-x86_64.AppImage",
        "Verified": "no"
    },
    "Floorp Nightly"  :{
        "url": "https://github.com/Portable-Linux-Apps/floorp-AppImage/releases/download/nightly/Floorp-v12.1.3-x86_64.AppImage",
        "Verified": "no"
    },
    "Palemoon" :{
        "url": "https://github.com/Portable-Linux-Apps/palemoon-AppImage/releases/download/33.8.2%402025-09-01_1756744100/Pale_Moon-33.8.2-x86_64.AppImage",
        "Verified": "no"
    },
    "Mullvad" :{
        "url": "https://github.com/Portable-Linux-Apps/mullvad-browser-AppImage/releases/download/14.5.6%402025-09-01_1756743924/Mullvad_Browser-14.5.6-x86_64.AppImage",
        "Verified": "no"
    },
    "Lapce" :{
        "url": "https://github.com/Portable-Linux-Apps/lapce-AppImage/releases/download/v0.4.4%402025-09-01_1756743889/Lapce-v0.4.4-x86_64.AppImage",
        "Verified": "no",
        "arm64": "https://github.com/Portable-Linux-Apps/lapce-AppImage/releases/download/v0.4.4%402025-09-01_1756743889/Lapce-v0.4.4-aarch64.AppImage"
    },
    "Ruffle" :{
        "url": "https://github.com/Portable-Linux-Apps/ruffle-AppImage/releases/download/nightly-2025-09-01%402025-09-01_1756743595/Ruffle-nightly-2025-09-01-x86_64.AppImage",
        "Verified": "no"
    },
    "Waterfox" :{
        "url": "https://github.com/Portable-Linux-Apps/Waterfox-AppImage/releases/download/140.3.0%402025-09-01_1756743590/Waterfox-140.3.0-x86_64.AppImage",
        "Verified": "no"
    },
    "Telegram"  :{
        "url": "https://github.com/Portable-Linux-Apps/Telegram-AppImage/releases/download/v6.1.0%402025-09-01_1756743380/Telegram-v6.1.0-x86_64.AppImage",
        "Verified": "no"
    },
    "Fastfetch" :{
        "url": "https://github.com/Portable-Linux-Apps/fastfetch-AppImage/releases/download/2.51.1%402025-09-01_1756743263/fastfetch-2.51.1-x86_64.AppImage",
        "Verified": "no",
        "arm64": "https://github.com/Portable-Linux-Apps/fastfetch-AppImage/releases/download/2.51.1%402025-09-01_1756743263/fastfetch-2.51.1-aarch64.AppImage"
    },
    "Lorien" :{
        "url": "https://github.com/Portable-Linux-Apps/Lorien-AppImage/releases/download/v0.6.0%402025-09-01_1756743231/Lorien-v0.6.0-x86_64.AppImage",
        "Verified": "no"
    },
    "IceCat" :{
        "url": "https://github.com/Portable-Linux-Apps/IceCat-AppImage/releases/download/128.14.0%402025-09-01_1756742510/IceCat-128.14.0-x86_64.AppImage",
        "Verified": "no"
    },
    "FireDragon Catppuccin" :{
        "url": "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-catppuccin-appimage-x64.AppImage",
        "Verified": "yes",
        "arm64": "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-catppuccin-appimage-arm64.AppImage"
    },
    "FireDragon" :{
        "url": "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-appimage-x64.AppImage",
        "Verified": "yes",
        "arm64": "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-appimage-arm64.AppImage"
    },
    "InkScape" :{
        "url": "https://inkscape.org/gallery/item/56343/Inkscape-ebf0e94-x86_64.AppImage",
        "Verified": "yes"
    },
    "Kdenlive" :{
        "url": "https://download.kde.org/stable/kdenlive/25.08/linux/kdenlive-25.08.0-x86_64.AppImage",
        "Verified": "yes"
    },
    "Kdenlive Daily" :{
        "url": "https://cdn.kde.org/ci-builds/multimedia/kdenlive/master/linux/kdenlive-master-10989-linux-gcc-x86_64.AppImage",
        "Verified": "yes"
    },
    "Shotcut" :{
        "url": "https://downloads.sourceforge.net/project/shotcut/v25.08.16/shotcut-linux-x86_64-250816.AppImage?ts=gAAAAABotzMu37rX1sMTx3RYUY3fq936BVa2Oyg6OxDQNQI3dog6Fog7EphWlXbuTbwfkyl8QqVDpfBhxLCB22gk7xpPbD97Eg%3D%3D&r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fshotcut%2Ffiles%2Fv25.08.16%2Fshotcut-linux-x86_64-250816.AppImage%2Fdownload",
        "Verified": "no"
    },
    "Openshot" :{
        "url": "https://github.com/OpenShot/openshot-qt/releases/download/v3.3.0/OpenShot-v3.3.0-x86_64.AppImage",
        "Verified": "yes"
    },
    "OBS Studio" :{
        "url": "https://github.com/pkgforge-dev/OBS-Studio-AppImage/releases/download/31.1.2-1%402025-09-01_1756711907/OBS-Studio-31.1.2-1-anylinux-x86_64.AppImage",
        "Verified": "no"
    },
    "Virtual Box" :{
        "url": "https://github.com/ivan-hc/VirtualBox-appimage/releases/download/20250904-142056/VirtualBox-KVM_7.2.0-archimage4.3-x86_64.AppImage",
        "Verified": "no"
    },
    "Discord" :{
        "url": "https://github.com/simoniz0r/Discord-AppImage/releases/download/discord-stable/discord-x86_64.AppImage",
        "Verified": "no"
    },
    "Discord PTB" :{
        "url": "https://github.com/simoniz0r/Discord-AppImage/releases/download/discord-ptb/discord-ptb-x86_64.AppImage",
        "Verified": "no"
    },
    "Discord Canary" :{
        "url": "https://github.com/simoniz0r/Discord-AppImage/releases/download/discord-canary/discord-canary-x86_64.AppImage",
        "Verified": "no"
    },
    "Slack" :{
        "url": "https://gitlab.com/linuxappimage/slack-desktop/-/jobs/artifacts/master/raw/Slack-x86_64.AppImage?job=run-build",
        "Verified": "yes"
    },
    "Libre Office" :{
        "url": "https://appimages.libreitalia.org/LibreOffice-fresh.full-x86_64.AppImage",
        "Verified": "yes"
    },
    "OnlyOffice" :{
        "url": "https://github.com/ONLYOFFICE/appimage-desktopeditors/releases/download/v9.0.4/DesktopEditors-x86_64.AppImage",
        "Verified": "yes"
    },
    "QEMU" :{
        "url": "https://github.com/DanielMYT/qemu-appimage/releases/download/10.1.0/qemu-10.1.0-x86_64.AppImage",
        "Verified": "no"
    },
    "Darktable" :{
        "url": "https://github.com/darktable-org/darktable/releases/download/release-5.2.1/Darktable-5.2.1-x86_64.AppImage",
        "Verified": "yes"
    },
    "Handbrake" :{
        "url": "https://github.com/ivan-hc/Handbrake-appimage/releases/download/continuous/HandBrake_1.10.1-1-archimage4.3-x86_64.AppImage",
        "Verified": "no"
    },
    "Olive Video Editor" :{
        "url": "https://github.com/olive-editor/olive/releases/download/0.2.0-nightly/Olive-8ac191ce-Linux-x86_64.AppImage",
        "Verified": "yes"
    },
    "Linux MultiMedia Studio" :{
        "url": "https://github.com/LMMS/lmms/releases/download/v1.2.2/lmms-1.2.2-linux-x86_64.AppImage",
        "Verified": "yes"
    },
    "Linux MultiMedia Studio Alpha" :{
        "url": "https://github.com/LMMS/lmms/releases/download/v1.3.0-alpha.1/lmms-1.3.0-alpha.1.102%2Bg89fc6c9-linux-x86_64.AppImage",
        "Verified": "yes"
    },
    "Hydrogen" :{
        "url": "https://github.com/hydrogen-music/hydrogen/releases/download/1.2.6/Hydrogen-1.2.6-x86_64.AppImage",
        "Verified": "yes"
    },
    "Calibre" :{
        "url": "https://github.com/KushagraKarira/calibre-appimage/releases/download/v8.4.0/Calibre-8.4.0-x86_64.AppImage",
        "Verified": "no"
    },
    "Zotero" :{
        "url": "https://github.com/ryuuzaki42/Zotero_AppImage/releases/download/7.0.24/Zotero-7.0.24-1_JB-x86_64.AppImage",
        "Verified": "no"
    },
    "Obsidian" :{
        "url": "https://github.com/obsidianmd/obsidian-releases/releases/download/v1.9.12/Obsidian-1.9.12.AppImage",
        "Verified": "yes",
        "arm64": "https://github.com/obsidianmd/obsidian-releases/releases/download/v1.9.12/Obsidian-1.9.12-arm64.AppImage"
    },

    "Wireshark" :{
        "url": "https://github.com/ryuuzaki42/Wireshark_AppImage/releases/download/4.4.8/Wireshark-4.4.8.glibc2.29-x86_64-1_JB.AppImage",
        "Verified": "no"
    },
    "nmap" :{
        "url": "https://github.com/iTrooz/nmap-appimage/releases/download/7.95/nmap-7.95-x86_64.AppImage",
        "Verified": "no"
    },
    "KeePassXC" :{
        "url": "https://github.com/keepassxreboot/keepassxc/releases/download/2.7.10/KeePassXC-2.7.10-x86_64.AppImage",
        "Verified": "yes"
    },
    "Modrinth" :{
        "url": "https://launcher-files.modrinth.com/versions/0.10.7/linux/Modrinth%20App_0.10.7_amd64.AppImage",
        "Verified": "yes"
    },
    "Prism luncher" :{
        "url": "https://github.com/PrismLauncher/PrismLauncher/releases/download/9.4/PrismLauncher-Linux-x86_64.AppImage",
        "Verified": "yes"
    },
    "Steam" :{
        "url": "https://github.com/ivan-hc/Steam-appimage/releases/download/1.0.0.82-2%402025-09-01_1756708218/Steam-1.0.0.82-2-anylinux-x86_64.AppImage",
        "Verified": "no"
    },
    "Microsoft Edge" :{
        "url": "https://github.com/ivan-hc/MS-Edge-appimage/releases/download/continuous/Microsoft-Edge-stable-139.0.3405.125-1-x86_64.AppImage",
        "Verified": "no"
    },
    "Microsoft Edge Beta" :{
        "url": "https://github.com/ivan-hc/MS-Edge-appimage/releases/download/continuous/Microsoft-Edge-beta-140.0.3485.49-1-x86_64.AppImage",
        "Verified": "no"
    },
    "Microsoft Edge Dev" :{
        "url": "https://github.com/ivan-hc/MS-Edge-appimage/releases/download/continuous/Microsoft-Edge-dev-141.0.3525.0-1-x86_64.AppImage",
        "Verified": "no"
    },
    "Vivaldi" :{
        "url": "https://github.com/ivan-hc/Vivaldi-appimage/releases/download/continuous/Vivaldi-stable-7.5.3735.66-1-x86_64.AppImage",
        "Verified": "no",
        "arm64": "https://github.com/ivan-hc/Vivaldi-appimage/releases/download/continuous/Vivaldi-stable-7.5.3735.66-1-aarch64.AppImage"
    },
    "Vivaldi snapshot" :{
        "url": "https://github.com/ivan-hc/Vivaldi-appimage/releases/download/continuous/Vivaldi-snapshot-7.6.3797.27-1-x86_64.AppImage",
        "Verified": "no",
        "arm64": "https://github.com/ivan-hc/Vivaldi-appimage/releases/download/continuous/Vivaldi-snapshot-7.6.3797.27-1-aarch64.AppImage"
    },
}

aim_path = shutil.which("aim")
home_directory = os.path.expanduser("~")
appimage_directory = os.path.join(home_directory, "appimages")
os.makedirs(appimage_directory, exist_ok=True)
aim_download = "https://raw.githubusercontent.com/143domi1/aim/refs/heads/main/aim"
version = 0.3

try:
    command = sys.argv[1]
except IndexError:
    print("ERROR 1 - Please enter a command!\nIf you need help, please enter the help command")
    sys.exit(1)


if command == "install":
    try:
        app = sys.argv[2]
    except IndexError:
        print("ERROR 1 - Please enter the app name!\nIf you need help, please enter the help command")
        sys.exit(1)
    if app in apps:
        arhitecture = platform.machine().lower()
        if arhitecture == "x86_64":
            url_download = apps[app].get("url")
        elif arhitecture == "amd64":
            url_download = apps[app].get("url")
        elif arhitecture == "aarch64":
            url_download = apps[app].get("arm64")
        elif arhitecture == "armv7l":
            url_download = apps[app].get("arm32")
        elif arhitecture == "riscv64":
            url_download = apps[app].get("risc-v")
        if url_download is None:
            print(f"Sorry,{app} does not support the {arhitecture} arhitecture you are using.")
            sys.exit(1)
        filename = os.path.join(appimage_directory, url_download.split("/")[-1])
        if os.path.exists(filename):
            print(f"{app} is already installed.")
        else:
            if apps[app]["Verified"] == "yes":
                print("Downloading..(Don't worry if it takes a long time)")
                response = requests.get(url_download, stream=True)
                with open(filename, "wb") as f:
                    for chunk in response.iter_content(chunk_size=524288):
                        if chunk:
                            f.write(chunk)
                os.chmod(filename, 0o755)
                print(f"{app} is stored in {filename}")
            elif apps[app]["Verified"] == "no":
                print(f"Warning, {app} is not verified by the AIM team, this means that this app has been repackaged by someone outside the original developers for the app!")
                answer = input("Do you wish to continue?\ny - yes,n - no\n")
                if answer == "y":
                    print("Downloading..(Don't worry if it takes a long time)")
                    response = requests.get(url_download, stream=True)
                    with open(filename, "wb") as f:
                        for chunk in response.iter_content(chunk_size=524288):
                            if chunk:
                                f.write(chunk)
                    os.chmod(filename, 0o755)
                    print(f"{app} is stored in {filename}")
    else: 
        print(f"{app} does not exist.")
elif command == "info":
    arhitecture = platform.machine()
    print(f"AIM – AppImage Installer/Manager \nCopyright (c) 2025 143domi1 (Github username) \nLicensed under the GNU General Public License v3.0 (GPLv3) \nThis program is fully FOSS (Free and open source software). \nLicense details: https://github.com/143domi1/aim/blob/main/LICENSE\nVersion: {version}\nArhitecture: {arhitecture}")

elif command == "list":
    files = [f for f in os.listdir(appimage_directory) if os.path.isfile(os.path.join(appimage_directory, f))]
    files.sort(key=lambda f: os.path.getmtime(os.path.join(appimage_directory, f)), reverse=True)
    print("Installed AppImages: ")
    for f in files:
        print(f)
elif command == "delete":
    try:
        app = sys.argv[2]
    except IndexError:
        print("ERROR 1 - Please enter the app name!\nIf you need help, please enter the help command")
        sys.exit(1)
    app_to_delete = app
    file_to_delete = os.path.join(appimage_directory, app_to_delete)

    if not os.path.exists(appimage_directory):
        print("No Appimages exist")
    if os.path.isfile(file_to_delete):
        os.remove(file_to_delete)
        print(f"{app_to_delete} has been deleted.")
    else:
        print(f"{app_to_delete} is not installed.")
elif command == "upgrade":
    print("Upgrading aim..")
    if aim_path is None:
        print("Aim not found in path")
    else:
        upgrade_aim = requests.get(aim_download, stream=True)
        user_path = os.path.expanduser("~/.local/bin/aim")
        global_path = "/usr/local/bin/aim"
        if aim_path == global_path :
            with open(global_path, "wb") as f:
                for chunk in upgrade_aim.iter_content(chunk_size=262144):
                    if chunk:
                        f.write(chunk)
            os.chmod(global_path, 0o755)
            print(f"Aim has been upgraded.")
        elif aim_path == user_path:
            with open(user_path, "wb") as f:
                for chunk in upgrade_aim.iter_content(chunk_size=262144):
                    if chunk:
                        f.write(chunk)
            os.chmod(user_path, 0o755)
            print("Aim has been upgraded")
elif command == "applist":
    question = input("Are you sure you want to see the whole applist of AIM?\ny - yes, n - no\n")
    question.lower()
    if question == "y":
        for app in apps:
            print(f"{app}")
    elif question == "n":
        sys.exit(0)
elif command == "run":
    app = sys.argv[2]
    app_path = os.path.join(appimage_directory, app)
    if os.path.isfile(app_path):
        subprocess.Popen([app_path])
    else:
        print(f"ERROR 3 - {app} is not installed!")

elif command == "help":
    print("These are all the commands in aim: ")
    print("aim install <appname> - Installs the specified app. ")
    print("aim info - Gives information about aim.")
    print("aim list - This command lists all appimage programs.")
    print("aim delete <appname> - Deletes the specified app.")
    print("aim upgrade - This command upgrades aim on your system.")
    print("aim applist - This command tells you all the apps currently available in AIM.")
    print("aim run <appname> - This command allows you to run apps installed via aim.")
    print("aim help - The help command.")

