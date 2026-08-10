

# FATC0RK's BypassNRO Script

From the OOBE Screen press Shift + F10
**MAKE SURE TO CLICK ON THE CMD WINDOW**

```
curl -L https://raw.githubusercontent.com/FATC0RK/BYPASSNRO/refs/heads/main/bypass.cmd -o skip.cmd
skip.cmd
```

# What it Does

**Setup / OOBE**

-   Accepts EULA automatically, placeholder product key (prompts only on activation error)
-   Hides EULA page, OEM registration screen, online account screens, and Wi-Fi setup screen
-   `ProtectYourPC = 3` (minimal telemetry option shown/selected)

**User account**
-   Creates **one** local account: `USER`, in the Administrators group, blank password
-   Auto-logs in as `USER` for the first login only

**AppX packages removed** 
3D Viewer, Bing Search, Camera, Clipchamp, Copilot, Dev Home, Family Safety, Feedback Hub, Game Assist, Get Help, Get Started, Mail & Calendar, Maps, Mixed Reality Portal, News, Notepad (Store version), Office Hub, OneNote, Outlook for Windows, Paint 3D, People, Photos, Power Automate Desktop, Quick Assist, Skype, Solitaire Collection, Teams/MSTeams, To Do, Voice Recorder, Wallet, Weather, Xbox apps (all variants), Zune Music, Zune Video _(Sticky Notes kept for stylus/Ink Workspace)_

**Windows capabilities removed** 
Fax & Scan, Internet Explorer, OneSync, OpenSSH Client, PowerShell ISE, Quick Assist, Speech, Text-to-Speech, Steps Recorder, Windows Media Player, WordPad _(Handwriting, MathRecognizer, and all three Windows Hello Face capabilities kept)_

**Optional features removed** 
Media Playback, PowerShell v2, Remote Desktop Connection client, Recall

**Registry / system tweaks — Specialize phase**

-   Removes DevHome/Outlook auto-update scheduled tasks
-   Restores classic "New Text Document" behavior
-   Deletes OneDrive shortcut and setup executables
-   Disables auto-install of Chat/Teams icon
-   Enables NTFS long path support
-   Disables "News and Interests"
-   Sets empty Start menu pin layout

**Default User hive (applies to new profiles)**

-   Disables Copilot
-   Clears an audio property store key
-   Disables Notepad's "Get more in Store" banner
-   Removes OneDrive from startup
-   Disables Xbox Game Bar capture
-   Hides Task View button
-   Disables search box suggestions
-   Schedules `UserOnce.ps1` via RunOnce for each new user's first login

**Per-user first login** (`UserOnce.ps1`)
-   Disables taskbar search box
-   Restarts Explorer to apply it

**Final cleanup** (`FirstLogon.ps1`)
-   Resets autologon count to 0
-   Deletes `C:\Windows.old`
-   Deletes `unattend.xml`, `unattend-original.xml`, `Wifi.xml` from disk
