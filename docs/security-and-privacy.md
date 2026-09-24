# Blue Runner security and privacy

This description reflects the inspected v1.1.5 application and Windows installer. It describes Blue Runner's own implementation, not the behavior or privacy practices of DCS, configured utilities, Windows, browsers, or external services.

## Launching applications and privileges

Blue Runner launches DCS in 2D or VR and launches user-configured Windows applications, scripts, shortcuts, folders, and HTTP/HTTPS links. Utility configuration includes raw launch parameters, dependencies, startup delays, and minimized/admin settings. Treat configuration and configured scripts as trusted executable instructions; do not import commands from untrusted people.

Normal operation is designed for a standard Windows user. Blue Runner does not automatically elevate itself at startup or after saving configuration. Individual admin-marked launches request Windows UAC approval through a launch helper. Eligible selected admin utilities share one UAC prompt. If Blue Runner is already elevated, standard-user launches use the interactive desktop shell token; they fail if the required token is unavailable. This is not a guarantee for every third-party launcher or cross-account setup.

Stop operations can forcibly terminate processes by PID and executable image, including dependency chains and background/tray applications. Image-based stopping can affect multiple instances. Elevated stops request UAC where needed; selected admin stops can be grouped. Explorer has a stop guard. Process/window discovery and bounded window minimization operate during utility startup. Optional DCS CPU affinity changes use Windows process APIs.

The inspected application has no process injection, DLL injection, DCS hook installation, persistent privileged service, or driver implementation. It starts processes, inspects process state/windows, sets affinity when requested, and invokes Windows termination commands. This statement does not cover launched utilities.

## Configuration and local data

`blue_runner_config.json` is plaintext beside the installed executable (or script for source operation). It stores DCS/Saved Games paths; DCS arguments, affinity and admin settings; utility names, IDs, executable/target paths, parameters, selection, admin/minimized flags, dependencies and delays; and UI size/theme settings. Paths and parameters may contain personal or sensitive data. Blue Runner does not encrypt this file. Do not store secrets in launch arguments.

The app creates missing configuration, normalizes loaded values, and saves settings on relevant actions and shutdown. An invalid configuration may be renamed to `blue_runner_config.corrupt.json` before defaults are written. Existing valid configuration is not rewritten merely by loading it. Auto-detection can fill missing local DCS paths. Distribution includes a sanitized sample, not a developer's live configuration.

Backups live beside the app as `MissionScripting.lua.backup`, `Export.lua.backup`, `Options.lua.backup`, and `Input.backup.zip`. Launch helpers use temporary JSON request/result files containing target paths and parameters; elevated grouped stopping uses a temporary command file. Normal cleanup is attempted; these are not encrypted storage. Maintenance messages and process status are shown in the UI. The installer also writes local installation logs under `%LOCALAPPDATA%\BlueZone Tools\Installer Logs`.

## DCS maintenance and deletion

These operations are initiated through application controls and depend on the configured folders and current Windows permissions:

- Update/Repair launches the installed `bin\DCS_updater.exe` with `update` or `repair`. That external updater can download and change DCS files.
- Clear Shaders removes and recreates the `fxo` and `metashaders2` folders under the configured Saved Games folder.
- Backup copies DCS `Scripts\MissionScripting.lua`, Saved Games `Scripts\Export.lua`, and `Config\options.lua` to local backups. Restore overwrites the corresponding target from its backup. Review compares contents.
- Controller backup archives Saved Games `Config\Input`. Restore replaces the current Input directory with the backup ZIP after confirmation; it does not merge settings.
- Tracks/Logs controls delete selected files or files older than the chosen age. Track scanning is recursive under `Tracks\Multiplayer`; `lastMissionTrack.trk` and `tempMission.miz.trk` are excluded. Crash cleanup covers `*.crash`, `*.dmp`, and `*.zip` under `Logs`.

Blue Runner does not automatically append integration code to `Export.lua`. Its explicit Restore action can overwrite that file with `Export.lua.backup`, including whatever third-party code the backup contains. Likewise, restoring MissionScripting.lua restores the saved file; the UI label “Script Sanitizing” does not mean Blue Runner automatically rewrites sanitization statements. Backups and deletion actions require care: restored files can change DCS behavior and deletions are not a recycle-bin workflow.

## Network access

Public-IP detection runs on startup and on Refresh. It tries these HTTPS endpoints in order until one returns a valid IP address, using a four-second timeout per request:

1. `https://api.ipify.org`
2. `https://ifconfig.me/ip`
3. `https://icanhazip.com`
4. `https://checkip.amazonaws.com`

Requests include a `User-Agent` identifying Blue Runner and its version (`Blue Runner/v1.1.5`). The service receives the request's public source IP and normal network/request metadata. The code does not attach configuration, DCS files, backups, or logs. Service-side logging and retention are outside Blue Runner's control. Mask/Unmask changes only the displayed value: it does not prevent requests or hide the IP from the service. Masking is session-only; IPv4 keeps its first octet and IPv6 is hidden entirely.

User-activated browser links include:

- CPU affinity calculator: `https://bitsum.com/tools/cpu-affinity-calculator/`
- Ko-fi: `https://ko-fi.com/bluezone116`
- PayPal: `https://paypal.me/bluezone116`
- Patreon: `https://www.patreon.com/bluezone116`

Installer publisher/support metadata points to `https://bluezonetools.com`. Configured HTTP/HTTPS utility targets open through Windows Shell/browser behavior and can contact other destinations.

No telemetry uploader, analytics SDK, automatic Blue Runner update check, or automatic Blue Runner download mechanism was found in the inspected application. Public-IP lookup is automatic network activity. DCS Update/Repair is a separate user-triggered external updater; utilities and browsers have their own networking behavior.

## Registry and installation

Runtime path detection reads Windows registry information for Eagle Dynamics, Steam, Saved Games/user-profile paths, and PowerShell discovery. No runtime registry-writing implementation was found. The installer requires administrator privileges, registers installation/uninstall metadata, reads existing install locations, and removes stale Blue Runner uninstall registry entries whose uninstaller is missing. It creates shared Start Menu shortcuts and an optional Desktop shortcut.

The installer excludes live configuration and reuses existing installation paths during upgrades. Its optional finish-page launch uses the original user context. Uninstall asks whether to delete settings and leftover files; accepting permits recursive cleanup of the installation directory, including configuration and backups. Declining retains user data while installed application files are removed.

Some maintenance writes may require additional Windows permissions depending on folder ownership. Blue Runner does not require administrator privileges for normal operation. Operations or applications configured to require elevation request Windows UAC approval when needed. This document is a source inspection summary, not an independent security audit or a guarantee that compiled software cannot be reverse engineered.
