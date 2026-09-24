# 🚀 Blue Runner

<p align="center">

![GitHub Release](https://img.shields.io/github/v/release/bluexone116/BlueRunner?style=for-the-badge&logo=github&label=Release)
![GitHub Downloads](https://img.shields.io/github/downloads/bluexone116/BlueRunner/total?style=for-the-badge&logo=github&label=Downloads)
![GitHub Stars](https://img.shields.io/github/stars/bluexone116/BlueRunner?style=for-the-badge&logo=github&label=Stars)
![GitHub Issues](https://img.shields.io/github/issues/bluexone116/BlueRunner?style=for-the-badge&logo=github&label=Issues)
![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-blue?style=for-the-badge&logo=windows)

</p>

> **A streamlined Windows launcher and utility manager built for DCS World pilots.**

Blue Runner brings your DCS launch options, supporting applications, startup sequencing, and maintenance tools together in one clean interface.

Instead of opening multiple programs, waiting for one utility before starting another, browsing through folders, and remembering maintenance procedures before every flight, Blue Runner gives you one central control panel to prepare your system and get flying.

---

# ✨ What's New in v1.1.5

Blue Runner v1.1.5 significantly expands application startup and management.

### 🔗 Application Dependencies

Utilities can depend on other utilities.

For example:

`Tablet Driver → OpenKneeboard → Other Utility`

Blue Runner automatically starts dependencies in the correct order.

Dependency chains can include multiple levels, and Blue Runner prevents circular dependency configurations.

### ⏱️ Startup Delays

Each utility can have its own startup delay from **0–15 seconds**.

This is useful when one application needs time to initialize before the next application starts.

### 🪟 Launch Minimized

Utilities can be configured to start minimized.

Blue Runner monitors newly launched applications for a short startup period so applications that create their windows after launch can still be minimized.

After startup, the application can be restored normally by the user.

### 🛡️ Per-Application Administrator Control

Administrator access can now be configured individually.

Each utility can independently use:

`RunAs Admin`

DCS can also be configured separately to run elevated.

Blue Runner itself is designed to run normally without requiring permanent Administrator privileges.

### ↕️ Drag-and-Drop Utility Ordering

Utility rows in the Config tab can be reordered using the **↕ Drag** control.

The new order is reflected on the Apps tab and is saved with your configuration.

### 🔄 Full Dependency Start and Stop

**Start**, **Launch Selected**, **Stop**, and **Stop Selected** understand dependency chains.

Blue Runner can:

* Reuse applications that are already running
* Avoid launching shared dependencies multiple times
* Honor each application's delay, minimized, and Administrator settings
* Cancel pending delayed launches when a chain is stopped
* Stop dependent application chains
* Handle many tray applications that do not display a normal window

---

# 🎮 Application Launcher

Launch and manage your essential DCS applications from one place.

Blue Runner can manage applications such as:

* 🎙️ VoiceAttack
* 💬 Discord
* 🎯 DCS-DTC
* 🖥️ Virtual Desktop Streamer
* 🎥 TrackIR
* 📡 SimpleRadio Standalone (SRS)
* 📊 Tacview
* 🗺️ OpenKneeboard
* 🛠️ Custom user-configured applications

Applications can be:

* Enabled or disabled individually
* Started individually
* Stopped individually
* Started together using **Launch Selected**
* Stopped together using **Stop Selected**
* Configured with startup dependencies
* Given individual startup delays
* Launched minimized
* Configured to request Administrator privileges
* Reordered with drag-and-drop

Blue Runner tracks launched applications so they can be managed from the same interface.

---

# 🔗 Smart Startup Sequencing

Many DCS setups require applications to start in a particular order.

Blue Runner v1.1.5 can automate that process.

For each utility you can configure:

* **Dependency** — another utility that must start first
* **Delay** — wait 0–15 seconds before launch
* **Launch Minimized** — minimize its startup windows
* **RunAs Admin** — request elevation only for that application

Dependencies can form multi-level chains.

For example:

`Driver → OpenKneeboard → Supporting Utility`

When the final application is started, Blue Runner automatically works through the required chain.

This makes it possible to configure a complete pre-flight startup sequence and launch it with a single action.

---

# 🥽 DCS Launch Modes

Blue Runner provides dedicated launch options for different DCS configurations.

### 🖥️ Start DCS 2D

Launches DCS in standard monitor mode using:

`--force_disable_VR`

### 🥽 Start DCS VR

Launches DCS directly in VR mode using:

`--force_enable_VR`

No more manually changing VR settings before launching DCS.

DCS can also be configured independently to request Administrator privileges when required.

---

# ⚙️ CPU Affinity Support

Blue Runner includes optional CPU affinity control for DCS World.

Advanced users can:

* Enable or disable CPU affinity
* Configure a custom affinity mask
* Apply the configured processor affinity when DCS launches

> ⚠️ CPU affinity configuration is intended for advanced users. Incorrect settings may reduce performance.

---

# 🚀 Flexible Launch Support

Blue Runner's launch engine supports more than standard Windows executables.

Configured utilities can include:

* `.exe` applications
* PowerShell `.ps1` scripts
* Batch `.bat` files
* Command `.cmd` files
* Windows `.lnk` shortcuts
* HTTP/HTTPS URLs
* Folder targets

Command-line parameters are supported for applications that require them.

This allows Blue Runner to manage both normal DCS utilities and custom scripts or launcher workflows.

---

# 🧹 DCS Maintenance Tools

Blue Runner includes commonly used DCS maintenance functions.

Available tools include:

* 🔄 Update DCS World
* 🛠️ Run DCS Repair
* 🧹 Clear DCS shader caches
* 📂 Open the DCS installation folder
* 📁 Open the DCS Saved Games folder
* 💾 Backup `MissionScripting.lua`
* ♻️ Restore `MissionScripting.lua`
* 💾 Backup `Export.lua`
* ♻️ Restore `Export.lua`
* 🔍 Validate important backup files

Blue Runner can refresh backup status after DCS Update or Repair operations complete.

> 💡 Always maintain independent backups of important DCS files and configurations.

---

# 📁 Tracks and Logs

Blue Runner includes tools for reviewing and cleaning DCS-generated files.

The Tracks/Logs tools help manage items such as:

* DCS track files
* Crash-related files
* DCS log data

Files can be reviewed and selected before deletion, including multi-selection for cleanup.

This provides a convenient way to manage files that can accumulate over time in the DCS Saved Games directory.

---

# 🔧 Configuration

The Config tab provides centralized control over DCS and utility settings.

Configurable options include:

* 📁 DCS installation directory
* 📁 DCS Saved Games directory
* 🖥️ DCS 2D launch arguments
* 🥽 DCS VR launch arguments
* ⚙️ DCS CPU affinity
* 🛡️ DCS Administrator launch option
* 🚀 Utility names and commands
* 📝 Utility command-line parameters
* 🛡️ Per-utility Administrator control
* 🪟 Launch Minimized
* 🔗 Utility dependencies
* ⏱️ Startup delays
* ↕️ Utility ordering
* 🎮 Launch Selected startup selections

Settings are stored locally and restored when Blue Runner starts.

---

# 🔎 Automatic DCS Path Detection

Blue Runner can automatically locate common DCS installations and Saved Games folders.

Detection can use information from:

* Eagle Dynamics installation information
* Common DCS installation locations
* Steam libraries
* Windows Saved Games locations
* User profile locations

The Config tab includes an **Auto Detect DCS Paths** action.

Automatic detection fills missing paths without replacing paths you have already configured.

On a fresh installation, Blue Runner opens the Config tab so the detected paths and utility settings can be reviewed before use.

---

# 🌐 Public IP Display

Blue Runner can display your current public IP address in the application header.

Controls are provided to:

* Refresh the detected address
* Mask or unmask the displayed address

IPv4 masking hides the final portions of the address, while IPv6 addresses are hidden when masking is enabled.

Masking is session-only.

---

# 🖼️ Screenshots

![Blue Runner About Screen](docs/images/Blue%20Runner%20About%20Screen%20-%20small.png)

![Blue Runner Maintenance Window](docs/images/Blue%20Runner%20Maintenance%20Screen%20-%20small.png)

![Blue Runner Track-Log Window](docs/images/Blue%20Runner%20Track-Log%20screen%20-%20small.png)

![Blue Runner Config Window](docs/images/Blue%20Runner%20Config%20Screen%20-%20small.png)

---

# 📦 Installation

## Recommended Installation

1. Open the **Releases** section of this repository.
2. Download the latest Blue Runner installer.
3. Run the installer.
4. Review and accept the BlueZone EULA.
5. Follow the installation prompts.
6. Launch Blue Runner from the Start Menu or optional Desktop shortcut.
7. Open the Config tab and verify your DCS and application paths.

The installer preserves an existing Blue Runner configuration during upgrades.

---

# 🚀 First Run

When Blue Runner starts for the first time:

1. Open the **Config** tab if it is not already displayed.
2. Verify the detected DCS installation path.
3. Verify the DCS Saved Games path.
4. Configure the applications you want Blue Runner to manage.
5. Configure dependencies where one application must start before another.
6. Add startup delays where applications need additional initialization time.
7. Select **Launch Minimized** where desired.
8. Enable **RunAs Admin** only for applications that require elevation.
9. Drag utilities into your preferred display order.
10. Select the applications to include in **Launch Selected**.
11. Save your configuration.
12. Return to the **Apps** tab and launch your flight environment.

---

# 🗂️ Default Installation Location

The normal installation structure is:

`C:\BlueZone Tools\Blue Runner`

If an existing **BlueZone Tools** directory is detected on another fixed drive, the installer may reuse that shared BlueZone Tools location.

Users may also select a custom installation directory.

Blue Runner Start Menu shortcuts are placed under the shared **BlueZone Tools** program group.

---

# 🔒 Administrator Rights

Blue Runner is designed to run as a normal Windows user.

Administrator privileges are requested only when an operation or configured application requires them.

Individual utilities can be configured with:

`RunAs Admin`

DCS has its own Administrator launch option.

Elevated permissions may also be required for certain maintenance or process-management operations.

This approach allows applications that do not require elevation to continue running normally without inheriting Administrator privileges from Blue Runner.

If a Windows UAC request is declined, the associated elevated operation will not run.

---

# 🛡️ Safety and Backups

Blue Runner includes backup, restore, and validation tools for important DCS configuration files.

Before:

* Updating DCS
* Running major repairs
* Installing major modifications
* Changing scripting configuration
* Modifying export integrations

create or verify your backups.

Blue Runner makes these operations easier, but users should always maintain independent backups of important DCS files and configurations.

---

# 💾 Configuration and Upgrades

Your Blue Runner configuration is stored locally in:

`blue_runner_config.json`

It can contain machine-specific information such as:

* DCS paths
* Saved Games paths
* Utility commands and paths
* Startup selections
* Dependency settings
* Startup delays
* Minimized settings
* Administrator settings
* Window preferences

The installer does **not** ship a live user configuration and is designed to preserve an existing configuration during upgrades.

---

# 🖥️ System Requirements

* 🪟 Windows 10 or Windows 11
* ✈️ DCS World
* 💾 Approximately 100 MB of available storage
* 🔐 Administrator privileges only for features or applications that require them

Optional applications may include:

* VoiceAttack
* Discord
* DCS-DTC
* Virtual Desktop Streamer
* OpenKneeboard
* TrackIR
* Tacview
* SimpleRadio Standalone
* Other user-configured applications or scripts

---

# 🛠️ Built With

Blue Runner is developed using:

* 🐍 Python
* 🖼️ Tkinter
* 🪟 Windows APIs
* 📦 PyInstaller
* 📦 Inno Setup

---

# 🐞 Bug Reports

Found a problem?

When reporting an issue, please include:

* Blue Runner version
* Windows version
* DCS version
* Application or utility involved
* Description of the problem
* Steps required to reproduce the issue
* Screenshots or log information when available

Please use the repository **Issues** section for normal bug reports.

For security-related issues, please use the project's security reporting process rather than posting sensitive details in a public issue.

---

# 💡 Feature Requests

Ideas and suggestions are welcome.

Possible future improvements may include:

* 🔔 Application update notifications
* 📊 Enhanced system status monitoring
* 🧩 Additional DCS utility integrations
* 🎮 Expanded launcher profiles
* ☁️ Configuration backup and restore
* 🔄 Additional automatic application detection
* 📡 BlueZone service integration

Feature requests can be submitted through the repository **Issues** section.

---

# 📜 License

Blue Runner is proprietary software provided under the license included with the application and repository.

Please review the applicable license and EULA before redistributing the application.

---

# ⚠️ Disclaimer

Blue Runner is an independent community-developed utility.

It is not affiliated with or endorsed by Eagle Dynamics.

DCS World and associated names and trademarks are the property of their respective owners.

Use of this software is at your own risk. Always maintain backups of important files before performing updates, maintenance operations, or configuration changes.

---

# 💙 BlueZone

Blue Runner is part of the **BlueZone Tools** collection.

BlueZone develops tools and utilities designed to improve the DCS World experience for pilots, mission creators, server administrators, and communities.

### BlueZone Tools

* 🚀 **Blue Runner** — Application launcher and DCS utility manager
* 🧩 **Blue Mods** — DCS modification and maintenance tools
* 🖱️ **Blue Mouse** — Mouse support for OpenKneeboard in VR
* 📊 **BlueReel** — DCS event logging and analysis
* 🎞️ **Blue Replay** — DCS track replay control utility
* 🎬 **Other BlueZone utilities**

---

# 🤝 Support the Project

Blue Runner is developed and maintained as a free tool for the DCS community.

The goal is simple: make preparing for a flight easier by bringing application launching, startup sequencing, DCS maintenance, configuration, and other useful utilities together in one place.

Development, testing, documentation, and continued improvements all take time and resources. If Blue Runner makes your DCS setup easier and you would like to support its continued development, your contribution is greatly appreciated—but never expected.

### ☕ [Support on Ko-fi](https://ko-fi.com/bluezone116)

### 💙 [Support with PayPal](https://paypal.me/bluezone116)

### 🚀 [Join us on Patreon](https://www.patreon.com/bluezone116)

Every contribution helps support continued development, testing, and future improvements to Blue Runner and other BlueZone tools.

Thank you for using Blue Runner and supporting the BlueZone community. ✈️

---

# ✈️ Ready Room to Runway

**Configure. Sequence. Launch. Maintain. Fly.**

🚀 **Blue Runner — Your DCS flight environment, ready when you are.**
