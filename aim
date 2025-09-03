#!/usr/bin/env python3
import os
import requests
import shutil
import sys

apps = {
    "Auryo" : "https://github.com/sneljo1/auryo/releases/download/v2.5.4/Auryo-2.5.4.AppImage",
    "Audacity" : "https://github.com/audacity/audacity/releases/download/Audacity-3.7.5/audacity-linux-3.7.5-x64-22.04.AppImage",
    "CPod" : "https://github.com/z-------------/CPod/releases/download/v1.28.2/CPod-1.28.2-x86_64.AppImage",
    "Hypnos" : "https://hypnosplayer.org/download/beta6/Hypnos-nix-64bit-beta6_2019-07-14_b1.AppImage",
    "Melodie" : "https://github.com/feugy/melodie/releases/download/v2.0.0/melodie-2.0.0-x86_64.AppImage",
    "Pathephone" : "https://github.com/pathephone/pathephone-desktop/releases/download/v2.2.1/pathephone-desktop-2.2.1-x86_64.AppImage",
    "Poddr" : "https://github.com/Sn8z/Poddr/releases/download/v2.1.0/Poddr-2.1.0.AppImage",
    "QXGEdit" : "https://sourceforge.net/projects/qxgedit/files/qxgedit/1.0.1/qxgedit-1.0.1-2.1.x86_64.AppImage/download",
    "QmidiNet" : "https://sourceforge.net/projects/qmidinet/files/qmidinet/1.0.1/qmidinet-1.0.1-2.1.x86_64.AppImage/download",
    "Sharp Tunes" : "https://github.com/MD-AZMAL/Sharp-Tune/releases/download/v1.0.3/sharp-tune-1.0.3-x86_64.AppImage",
    "Sonic Lineup" : "https://code.soundsoftware.ac.uk/attachments/download/2766/SonicLineup-1.1-x86_64.AppImage",
    "Sonic Visualiser" : "https://code.soundsoftware.ac.uk/attachments/download/2880/SonicVisualiser-5.2.1-x86_64.AppImage",
    "Swag Lyrics" : "https://github.com/srevinsaju/swaglyrics-appimage/releases/download/latest/swaglyrics-x86_64.AppImage",
    "synthv1" : "https://sourceforge.net/projects/synthv1/files/synthv1/1.3.2/synthv1-jack-1.3.2-9.1.x86_64.AppImage/download",
    "Unofficial Sonos Controller for Linux" : "https://github.com/pascalopitz/unoffical-sonos-controller-for-linux/releases/download/v0.4.0-rc1/sonos-controller-unofficial-0.4.0-rc1.AppImage",
    "Unofficial Sonos Controller for Linux ARM64" : "https://github.com/pascalopitz/unoffical-sonos-controller-for-linux/releases/download/v0.4.0-rc1/sonos-controller-unofficial-0.4.0-rc1-arm64.AppImage",
    "Unofficial Sonos Controller for Linux ARMV7l" : "https://github.com/pascalopitz/unoffical-sonos-controller-for-linux/releases/download/v0.4.0-rc1/sonos-controller-unofficial-0.4.0-rc1-armv7l.AppImage",
    "Blowfish" : "https://github.com/kremalicious/blowfish/releases/download/v1.6.0/Blowfish-1.6.0.AppImage",
    "BunqDesktop" : "https://github.com/bunqCommunity/bunqDesktop/releases/download/0.9.10/bunqDesktop-0.9.10-x86_64.AppImage",
    "CRITERIA1D PRO" : "https://github.com/ARPA-SIMC/CRITERIA1D/releases/download/v1.8.7/CRITERIA1D_PRO-x86_64.AppImage",
    "Carpenters" : "https://github.com/uhlibraries-digital/carpenters/releases/download/v2.5.2/carpenters-2.5.2-x86_64.AppImage",
    "Elphyre-WalletShell" : "https://github.com/SpookyPool/elphyre-wallet-electron/releases/download/2.0.4/Elphyre-WalletShell-v2.0.4-linux.AppImage",
    "ExeQt" : "https://github.com/AlexandruIstrate/ExeQt/releases/download/v1.2.2/ExeQt-v1-2-2-x86_64.AppImage",
    "f-crm" : "https://github.com/jgaa/f-crm/releases/download/v0.2.0-beta/f-crm-x86_64-0.2.0.AppImage",
    "GitQlient" : "https://github.com/francescmaestre/GitQlient/releases/download/dev-latest/GitQlient-1.6.3-88-g2fb103c1-x86_64.AppImage",
    "goldendict" : "https://github.com/Abs62/goldendict/releases/download/continuous/GoldenDict-661dd4d-x86_64.AppImage",
    "Gospel Pdf viewer" : "https://github.com/ksharindam/gospel-pdf-viewer/releases/download/v3.2.0/Gospel_PDF-x86_64.AppImage",
    "Gosped Pdf viewer arm" : "https://github.com/ksharindam/gospel-pdf-viewer/releases/download/v3.2.0/Gospel_PDF-armhf.AppImage",
    "Munt" : "https://github.com/muntorg/munt-official/releases/download/v3.0.7/Munt-3.0.7-x64.AppImage",
    "Munt arm" : "https://github.com/muntorg/munt-official/releases/download/v3.0.7/Munt-lite-3.0.7-arm64.AppImage",
    "Blender" : "https://github.com/Lethja/blender-appimage/releases/download/2025-08-21/blender-4.5.2-x86_64.AppImage.zip",
    "Blender LTS" : "https://github.com/Lethja/blender-appimage/releases/download/2025-08-21/blender-4.2.13-x86_64.AppImage.zip",
    "Gimp" : "https://download.gimp.org/gimp/v3.0/linux/GIMP-3.0.4-x86_64.AppImage",
    "Gimp ARM64" : "https://download.gimp.org/gimp/v3.0/linux/GIMP-3.0.4-aarch64.AppImage",
    "Krita" : "https://download.kde.org/stable/krita/5.2.11/krita-5.2.11-x86_64.AppImage",
    "Krita Plus Nightly" : "https://cdn.kde.org/ci-builds/graphics/krita/krita-5.2/linux/krita-5.2.11-prealpha-135186cdd4-x86_64.AppImage",
    "Firefox" : "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox/firefox-142.0.r20250827004350-x86_64.AppImage",
    "Firefox Beta" : "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-beta/firefox-beta-143.0.r20250901090535-x86_64.AppImage",
    "Firefox Nightly" : "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-nightly/firefox-nightly-144.0.r20250902094807-x86_64.AppImage",
    "Firefox ESR" : "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-esr-next/firefox-esr-next-102.3.r20220912135840-x86_64.AppImage",
    "Firefox Developer Edition" : "https://github.com/srevinsaju/Firefox-Appimage/releases/download/firefox-devedition/firefox-devedition-143.0.r20250901090535-x86_64.AppImage",
    "Google Chrome" : "https://github.com/ivan-hc/Chrome-appimage/releases/download/continuous/Google-Chrome-stable-139.0.7258.154-1-x86_64.AppImage",
    "Google Chrome Beta" : "https://github.com/ivan-hc/Chrome-appimage/releases/download/continuous/Google-Chrome-beta-140.0.7339.41-1-x86_64.AppImage",
    "Google Chrome Unstable" : "https://github.com/ivan-hc/Chrome-appimage/releases/download/continuous/Google-Chrome-unstable-141.0.7378.3-1-x86_64.AppImage",
    "Brave Nightly" : "https://github.com/srevinsaju/Brave-AppImage/releases/download/v1.84.15/Brave-nightly-v1.84.15-x86_64.AppImage",
    "Brave Beta" : "https://github.com/srevinsaju/Brave-AppImage/releases/download/v1.83.88/Brave-beta-v1.83.88-x86_64.AppImage",
    "Brave" : "https://github.com/srevinsaju/Brave-AppImage/releases/download/v1.82.159/Brave-stable-v1.82.159-x86_64.AppImage",
    "htop" : "https://github.com/henry-hsieh/htop.appimage/releases/download/v3.3.0/Htop-x86_64.AppImage",
    "Visual Studio Code" : "https://github.com/valicm/VSCode-AppImage/releases/download/latest/VSCode-x86_64.AppImage",
    "Zen" : "https://github.com/zen-browser/desktop/releases/download/1.15.2b/zen-x86_64.AppImage",
    "Zen ARM" : "https://github.com/zen-browser/desktop/releases/download/1.15.2b/zen-aarch64.AppImage",
    "LibreWolf" : "https://gitlab.com/api/v4/projects/24386000/packages/generic/librewolf/142.0.1-1/LibreWolf.x86_64.AppImage",
    "LibreWolf ARM" : "https://gitlab.com/api/v4/projects/24386000/packages/generic/librewolf/142.0.1-1/LibreWolf.aarch64.AppImage",
    "Floorp" : "https://github.com/Portable-Linux-Apps/floorp-AppImage/releases/download/v12.1.3%402025-09-01_1756743432/Floorp-v12.1.3-x86_64.AppImage",
    "Floorp Nightly"  : "https://github.com/Portable-Linux-Apps/floorp-AppImage/releases/download/nightly/Floorp-v12.1.3-x86_64.AppImage",
    "Palemoon" : "https://github.com/Portable-Linux-Apps/palemoon-AppImage/releases/download/33.8.2%402025-09-01_1756744100/Pale_Moon-33.8.2-x86_64.AppImage",
    "Mullvad" : "https://github.com/Portable-Linux-Apps/mullvad-browser-AppImage/releases/download/14.5.6%402025-09-01_1756743924/Mullvad_Browser-14.5.6-x86_64.AppImage",
    "Lapce" : "https://github.com/Portable-Linux-Apps/lapce-AppImage/releases/download/v0.4.4%402025-09-01_1756743889/Lapce-v0.4.4-x86_64.AppImage",
    "Lapce ARM" : "https://github.com/Portable-Linux-Apps/lapce-AppImage/releases/download/v0.4.4%402025-09-01_1756743889/Lapce-v0.4.4-aarch64.AppImage",
    "Ruffle" : "https://github.com/Portable-Linux-Apps/ruffle-AppImage/releases/download/nightly-2025-09-01%402025-09-01_1756743595/Ruffle-nightly-2025-09-01-x86_64.AppImage",
    "Waterfox" : "https://github.com/Portable-Linux-Apps/Waterfox-AppImage/releases/download/140.3.0%402025-09-01_1756743590/Waterfox-140.3.0-x86_64.AppImage",
    "Telegram"  : "https://github.com/Portable-Linux-Apps/Telegram-AppImage/releases/download/v6.1.0%402025-09-01_1756743380/Telegram-v6.1.0-x86_64.AppImage",
    "Fastfetch" : "https://github.com/Portable-Linux-Apps/fastfetch-AppImage/releases/download/2.51.1%402025-09-01_1756743263/fastfetch-2.51.1-x86_64.AppImage",
    "Fastfetch ARM" : "https://github.com/Portable-Linux-Apps/fastfetch-AppImage/releases/download/2.51.1%402025-09-01_1756743263/fastfetch-2.51.1-aarch64.AppImage",
    "Lorien" : "https://github.com/Portable-Linux-Apps/Lorien-AppImage/releases/download/v0.6.0%402025-09-01_1756743231/Lorien-v0.6.0-x86_64.AppImage",
    "IceCat" : "https://github.com/Portable-Linux-Apps/IceCat-AppImage/releases/download/128.14.0%402025-09-01_1756742510/IceCat-128.14.0-x86_64.AppImage",
    "FireDragon Catppuccin" : "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-catppuccin-appimage-x64.AppImage",
    "FireDragon Catppuccin ARM" : "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-catppuccin-appimage-arm64.AppImage",
    "FireDragon" : "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-appimage-x64.AppImage",
    "FireDragon ARM" : "https://gitlab.com/garuda-linux/firedragon/firedragon12/-/releases/v12.2.1/downloads/firedragon-appimage-arm64.AppImage",
    "InkScape" : "https://inkscape.org/gallery/item/56343/Inkscape-ebf0e94-x86_64.AppImage",
    "Kdenlive" : "https://download.kde.org/stable/kdenlive/25.08/linux/kdenlive-25.08.0-x86_64.AppImage",
    "Kdenlive Daily" : "https://cdn.kde.org/ci-builds/multimedia/kdenlive/master/linux/kdenlive-master-10971-linux-gcc-x86_64.AppImage",
    "Shotcut" : "https://downloads.sourceforge.net/project/shotcut/v25.08.16/shotcut-linux-x86_64-250816.AppImage?ts=gAAAAABotzMu37rX1sMTx3RYUY3fq936BVa2Oyg6OxDQNQI3dog6Fog7EphWlXbuTbwfkyl8QqVDpfBhxLCB22gk7xpPbD97Eg%3D%3D&r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Fshotcut%2Ffiles%2Fv25.08.16%2Fshotcut-linux-x86_64-250816.AppImage%2Fdownload",
    "Openshot" : "https://github.com/OpenShot/openshot-qt/releases/download/v3.3.0/OpenShot-v3.3.0-x86_64.AppImage",
    "OBS Studio" : "https://github.com/pkgforge-dev/OBS-Studio-AppImage/releases/download/31.1.2-1%402025-09-01_1756711907/OBS-Studio-31.1.2-1-anylinux-x86_64.AppImage",
    "Virtual Box" : "https://github.com/ivan-hc/VirtualBox-appimage/releases/download/7.1.6/VirtualBox-KVM_7.1.6-archimage4.3-x86_64.AppImage",
    "Discord" : "https://github.com/simoniz0r/Discord-AppImage/releases/download/discord-stable/discord-x86_64.AppImage",
    "Discord PTB" : "https://github.com/simoniz0r/Discord-AppImage/releases/download/discord-ptb/discord-ptb-x86_64.AppImage",
    "Discord Canary" : "https://github.com/simoniz0r/Discord-AppImage/releases/download/discord-canary/discord-canary-x86_64.AppImage",
    "Slack" : "https://gitlab.com/linuxappimage/slack-desktop/-/jobs/artifacts/master/raw/Slack-x86_64.AppImage?job=run-build",
    "Libre Office" : "https://appimages.libreitalia.org/LibreOffice-fresh.full-x86_64.AppImage",
    "OnlyOffice" : "https://github.com/ONLYOFFICE/appimage-desktopeditors/releases/download/v9.0.4/DesktopEditors-x86_64.AppImage",
    "QEMU" : "https://github.com/DanielMYT/qemu-appimage/releases/download/10.1.0/qemu-10.1.0-x86_64.AppImage",
    "Darktable" : "https://github.com/darktable-org/darktable/releases/download/release-5.2.1/Darktable-5.2.1-x86_64.AppImage",
    "Handbrake" : "https://github.com/ivan-hc/Handbrake-appimage/releases/download/continuous/HandBrake_1.10.1-1-archimage4.3-x86_64.AppImage",
    "Olive Video Editor" : "https://github.com/olive-editor/olive/releases/download/0.2.0-nightly/Olive-8ac191ce-Linux-x86_64.AppImage",
    "Linux MultiMedia Studio" : "https://github.com/LMMS/lmms/releases/download/v1.2.2/lmms-1.2.2-linux-x86_64.AppImage",
    "Linux MultiMedia Studio Alpha" : "https://github.com/LMMS/lmms/releases/download/v1.3.0-alpha.1/lmms-1.3.0-alpha.1.102%2Bg89fc6c9-linux-x86_64.AppImage",
    "Hydrogen" : "https://github.com/hydrogen-music/hydrogen/releases/download/1.2.6/Hydrogen-1.2.6-x86_64.AppImage",
    "Calibre" : "https://github.com/KushagraKarira/calibre-appimage/releases/download/v8.4.0/Calibre-8.4.0-x86_64.AppImage",
    "Zotero" : "https://github.com/ryuuzaki42/Zotero_AppImage/releases/download/7.0.24/Zotero-7.0.24-1_JB-x86_64.AppImage",
    "Obsidian" : "https://github.com/obsidianmd/obsidian-releases/releases/download/v1.9.12/Obsidian-1.9.12.AppImage",
    "Obsidian ARM" : "https://github.com/obsidianmd/obsidian-releases/releases/download/v1.9.12/Obsidian-1.9.12-arm64.AppImage",
    "Wireshark" : "https://github.com/ryuuzaki42/Wireshark_AppImage/releases/download/4.4.8/Wireshark-4.4.8.glibc2.29-x86_64-1_JB.AppImage",
    "nmap" : "https://github.com/iTrooz/nmap-appimage/releases/download/7.95/nmap-7.95-x86_64.AppImage",
    "KeePassXC" : "https://github.com/keepassxreboot/keepassxc/releases/download/2.7.10/KeePassXC-2.7.10-x86_64.AppImage",
    "Modrinth" : "https://launcher-files.modrinth.com/versions/0.10.7/linux/Modrinth%20App_0.10.7_amd64.AppImage",
    "Prism luncher" : "https://github.com/PrismLauncher/PrismLauncher/releases/download/9.4/PrismLauncher-Linux-x86_64.AppImage",
    "Steam" : "https://github.com/ivan-hc/Steam-appimage/releases/download/1.0.0.82-2%402025-09-01_1756708218/Steam-1.0.0.82-2-anylinux-x86_64.AppImage",
    "Microsoft Edge" : "https://github.com/ivan-hc/MS-Edge-appimage/releases/download/continuous/Microsoft-Edge-stable-139.0.3405.125-1-x86_64.AppImage",
    "Microsoft Edge Beta" : "https://github.com/ivan-hc/MS-Edge-appimage/releases/download/continuous/Microsoft-Edge-beta-140.0.3485.40-1-x86_64.AppImage",
    "Microsoft Edge Dev" : "https://github.com/ivan-hc/MS-Edge-appimage/releases/download/continuous/Microsoft-Edge-dev-141.0.3514.0-1-x86_64.AppImage",
    }

aim_path = shutil.which("aim")
home_directory = os.path.expanduser("~")
appimage_directory = os.path.join(home_directory, "appimages")
os.makedirs(appimage_directory, exist_ok=True)
aim_download = "https://raw.githubusercontent.com/143domi1/aim/refs/heads/main/aim"


command = sys.argv[1]



if command == "install":
    app = sys.argv[2]
    if app in apps:
        url_download = apps[app]
        filename = os.path.join(appimage_directory, url_download.split("/")[-1])
        if os.path.exists(filename):
            print(f"{app} is already installed.")
        else:
            print("Downloading..(Don't worry if it takes a long time)")
            response = requests.get(url_download, stream=True)
            with open(filename, "wb") as f:
                for chunk in response.iter_content(chunk_size=524288):
                    if chunk:
                        f.write(chunk)
            os.chmod(filename, 0o755)
            print(f"{app}")
    else: 
        print(f"{app} does not exist.")
elif command == "info":
    print("AIM – AppImage Installer/Manager \nCopyright (c) 2025 143domi1 (Github username) \nLicensed under the GNU General Public License v3.0 (GPLv3) \nThis program is fully FOSS (Free and open source software). \nLicense details: https://github.com/143domi1/aim/blob/main/LICENSE")

elif command == "list":
    files = [f for f in os.listdir(appimage_directory) if os.path.isfile(os.path.join(appimage_directory, f))]
    files.sort(key=lambda f: os.path.getmtime(os.path.join(appimage_directory, f)), reverse=True)
    print("Installed AppImages: ")
    for f in files:
        print(f)
elif command == "delete":
    app = sys.argv[2]
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

elif command == "help":
    print("These are all the commands in aim: ")
    print("aim install - Installs the specified app. ")
    print("aim info - Gives information about aim.")
    print("aim list - This command lists all appimage programs.")
    print("aim delete - Deletes the specified app.")
    print("aim upgrade - This command upgrades aim on your system.")
    print("aim help - The help command.")
