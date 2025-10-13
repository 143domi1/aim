#!/usr/bin/env python3
required_packages = ["os", "shutil", "sys", "platform", "subprocess", "requests"]
try:
    import os
    import shutil
    import sys
    import platform
    import subprocess
    import requests
    import json
except ImportError:
    print("CRITICAL RUNTIME ERROR 5 - A critical libary is missing, this program requires the critical libary to be installed.\n What do you want to do?\n1.Let AIM download the required libary.\n2.Exit the program.")
    answer  = input("")
    if answer == "1":
        print("Downloading..")
        for package in required_packages:
            subprocess.call(["pip", "install", package])
    elif answer == "2":
        sys.exit(1)
aim_path = shutil.which("aim")
home_directory = os.path.expanduser("~")
share_directory = os.path.expanduser("~/.local/share") 
appimage_directory = os.path.join(home_directory, "appimages")
aim_directory = os.path.join(share_directory, "aim") 
os.makedirs(appimage_directory, exist_ok=True)
os.makedirs(aim_directory, exist_ok=True)
settings_download = "https://raw.githubusercontent.com/143domi1/aim/refs/heads/main/settings.json"
aim_download = "https://raw.githubusercontent.com/143domi1/aim/refs/heads/main/aim"
settings_pathh = os.path.expanduser("~/.local/share/aim/settings.json")
settings_path_global = "/var/lib/aim/settings.json" 
download_settings = requests.get(settings_download, stream=True)
paths_for_settings = [
    os.path.expanduser("~/.local/share/aim/settings.json"),
    "/var/lib/aim/settings.json"
]
settings_path = None
for spath in paths_for_settings:
    if os.path.exists(spath):
        settings_path = spath 
        break
try:
    if settings_path is None:
        raise FileNotFoundError("No settings file found.")
    with open(settings_path, "r") as settings:
        settings = json.load(settings)
        database_download = settings["url"]
except FileNotFoundError:
    print("Settings file has not been found!\nWould you like to download it?\n1.Download the settings file\n2.Exit the program")
    users_answer = input()
    if users_answer == "1":
        print("Where do you want it to be placed?\n1 for global\n2 for user")
        users_answer_for_path_for_settings = input()
        if users_answer_for_path_for_settings == "1":
            settings_response = requests.get(settings_download, stream=True)
            with open(settings_path_global, "wb") as f:
                for chunk in settings_response.iter_content(chunk_size=128):
                    if chunk:
                        f.write(chunk)
        elif users_answer_for_path_for_settings == "2":
            settings_response = requests.get(settings_download, stream=True)
            with open(settings_pathh, "wb") as f:
                for chunk in settings_response.iter_content(chunk_size=128):
                    if chunk:
                        f.write(chunk)
        print("Settings has successfuly been installed")
    elif users_answer == "2":
        sys.exit(1)
version = 0.5
database_path = os.path.expanduser("~/.local/share/aim/database.json")
database_path_global = "/var/lib/aim/database.json"
upgrade_database = requests.get(database_download, stream=True)
paths_for_db = [
    os.path.expanduser("~/.local/share/aim/database.json"),
    "/var/lib/aim/database.json"
    ]
db_path = None
for path in paths_for_db:
    if os.path.exists(path):
        db_path = path
        break

try:
    with open(database_path, "r") as apps:
        apps = json.load(apps)
except FileNotFoundError:
    print("Critical error - Database file has not been found\nWould you like to download it?\n1. Download the database file\n2. Exit the program")
    answer = input()
    if answer == "1":
        print("Where do you want it to be placed?\n1 for global\n2 for user")
        answerforpath = input()
        if answerforpath == "1":
            with open(database_path_global, "wb") as f:
                for chunk in upgrade_database.iter_content(chunk_size=128):
                    if chunk:
                        f.write(chunk)
        elif answerforpath == "2":
            with open(database_path, "wb") as f:
                for chunk in upgrade_database.iter_content(chunk_size=128):
                    if chunk:
                        f.write(chunk)
        print("Database has successfuly been installed")
    elif answer == "2":
        sys.exit(1)


except json.JSONDecodeError:
    print("Critical error - Something has gone terribly wrong!")

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
        architecture = platform.machine().lower()
        if architecture == "x86_64":
            url_download = apps[app].get("url")
        elif architecture == "amd64":
            url_download = apps[app].get("url")
        elif architecture == "aarch64":
            url_download = apps[app].get("arm64")
        elif architecture == "armv7l":
            url_download = apps[app].get("arm32")
        elif architecture == "riscv64":
            url_download = apps[app].get("risc-v")
        if url_download is None:
            print(f"Sorry,{app} does not support the {architecture} architecture you are using.")
            sys.exit(1)
        filename = os.path.join(appimage_directory, url_download.split("/")[-1])
        if os.path.exists(filename):
            print(f"{app} is already installed.")
        else:
            def app_download(url_download, filename, app):
                print("Downloading..(Don't worry if it takes a long time)")
                response = requests.get(url_download, stream=True)
                with open(filename, "wb") as f:
                    for chunk in response.iter_content(chunk_size=1048576):
                        if chunk:
                            f.write(chunk)
                os.chmod(filename, 0o755)
                print(f"{app} is stored in {filename}")
            if apps[app]["Verified"] == "yes":
                app_download(url_download, filename, app)
            elif apps[app]["Verified"] == "no":
                print(f"Warning, {app} is not verified by the AIM team, this means that this app has been repackaged by someone outside the original developers for the app!")
                answer = input("Do you wish to continue?\ny - yes,n - no\n")
                if answer == "y":
                    app_download(url_download, filename, app)
                elif answer == "n":
                    sys.exit(0)
    else: 
        print(f"{app} does not exist.")
elif command == "info":
    architecture = platform.machine()
    print(f"AIM – AppImage Installer/Manager \nCopyright (c) 2025 143domi1 (Github username) \nLicensed under the GNU General Public License v3.0 (GPLv3) \nThis program is fully FOSS (Free and open source software). \nLicense details: https://github.com/143domi1/aim/blob/main/LICENSE\nRepository: {settings["url"]}\nVersion: {version}\nArchitecture: {architecture}")

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
        upgrade_database = requests.get(database_download, stream=True) 
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
        if db_path == database_path:
            with open(database_path, "wb") as f:
                for chunk in upgrade_database.iter_content(chunk_size=128):
                    if chunk:
                        f.write(chunk)
        elif db_path == database_path_global:
            with open(database_path_global, "wb") as f:
                for chunk in upgrade_database.iter_content(chunk_size=128):
                    if chunk:
                        f.write(chunk)
            print("Aim has been upgraded")
elif command == "applist":
    question = input("Are you sure you want to see the whole applist of AIM?\ny - yes, n - no\n")
    question.lower()
    if question == "y":
        with open(database_path, "r") as apps:
            apps = json.load(apps)
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
    print("These are all the commands in aim:\naim install <appname> - Installs the specified app.\naim info - Gives information about aim.\naim list - This command lists all appimage programs.\naim delete <appname> - Deletes the specified app.\naim upgrade - This command upgrades aim on your system.\naim applist - This command tells you all the apps currently available in AIM.\naim run <appname> - This command allows you to run apps installed via aim.\naim help - The help command.")


