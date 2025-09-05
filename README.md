
**Automatically set beautiful, high-resolution wallpapers from Unsplash on your desktop. This free, open-source tool runs every hour, delivering fresh day and night-themed wallpapers tailored to your username and the time of day.**

---

### Key Features
- **Cross-Platform**: Works seamlessly on Windows, OSX and Linux.
- **Dynamic Themes**: Automatically fetches light-themed wallpapers during the day and dark-themed ones at night.
- **Personalized**: Tracks wallpapers provided to a user to ensure a fresh experience.
- **Hourly Updates**: Your desktop wallpaper is refreshed every hour, for free.
- **Lightweight**: A simple script with minimal dependencies.

---

### Getting Started

#### Prerequisites

Before you begin, ensure you have the required command-line tools installed.

- **For Debian/Ubuntu**:
`sudo apt-get update && sudo apt-get install curl jq`
- **For macOS (using Homebrew)**:
`brew install curl`
- **For Windows**:
The script uses built-in PowerShell commands, so no extra tools are needed.

#### Installation

1.  **Clone the repository**:
  ```
  cd ~
  git clone https://github.com/jeerovan/auto-wallpaper-changer.git
  cd auto-wallpaper-changer
  ```

2.  **Set up the automated task**:

  -   **Linux (systemd)**:
      1.  Make the script executable: `chmod +x Debian12/script.sh`
      2.  Customize the `script.sh` and `wallpaper.service` file to ensure the `TARGET_USER` and `USER` are correct.
      3.  Copy and enable the service:
          ```
          sudo cp wallpaper.* /etc/systemd/system/
          sudo systemctl daemon-reload
          sudo systemctl enable wallpaper.timer
          ```

  -   **macOS (launchd)**:
    1.  Customize the `script.sh` file with TargetUser and `com.jeerovan.comfer.plist` file with the correct path to the `script.sh` script.
    2.  Copy the plist to your LaunchAgents directory:
        ```
        cp com.jeerovan.comfer.plist ~/Library/LaunchAgents/
        launchctl load ~/Library/LaunchAgents/wallpaper.plist
        ```        

  -   **Windows (Task Scheduler)**:
    1.  Change NAME in the script Windows/script.ps1.
    2.  Open task scheduler (taskschd.msc) and Create a new task to run every hour.
    3.  Set the action to "Start a program" and use `powershell.exe` with the argument `-ExecutionPolicy Bypass -File "C:\Users\<USERNAME>\auto-wallpaper-changer\Windows\script.ps1"`.
---

### License

Distributed under the MIT License. See `LICENSE` for more information.

---

### Acknowledgments

-   **Unsplash** for providing the incredible collection of photos.
-   Uses the same API which powers [**Comfer Launcher**](https://play.google.com/store/apps/details?id=com.jeerovan.comfer)

