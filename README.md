# "Super God Mode" For Windows

This PowerShell script <b>creates shortcuts to all special shell folders, named folders, task links, system settings, deep links, and URL protocols in Windows</b>, providing easy access to a wide range of system settings and features.

It was inspired by the famously nicknamed "God Mode" folder and creates many more shortcuts than even that. 

➤ Note: It's not really a "mode", that's just a catchy name. Running this doesn't change any system settings, it just creates a folder containing a ton of shortcuts.

## Screenshots

<p align="center">
<img width="700" alt="GUI Window" src="https://github.com/user-attachments/assets/d318373c-d4d4-4521-bf57-8b4a4b4273ee">
</p><p align="center">
<img width="290" alt="Results" src="https://github.com/user-attachments/assets/4d01fbad-b597-4433-bd67-2638ded8a6ed">
<img width="392" alt="Output Folders" src="https://github.com/user-attachments/assets/898efc48-ddc6-4875-b906-b89963d5778e">
</p>



## Features

- Creates shortcuts for various Windows components:
  - **CLSID Shell Folders**
  - **Named Special Folders**
  - **Task Links** (sub-pages within shell folders and control panel menus)
  - **System settings** (ms-settings: links)
  - **"Deep Links"** (direct links to various settings menus across Windows)
  - **URL Protocols**
  - **Hidden App Links** (Internal-use and undocumented URL links used by apps)
- Generates CSV files with detailed information about the shortcuts
- Saves XML content retrieved from shell32.dll and other sources for reference
- Graphical User Interface (GUI) for easy configuration
- Release versions signed with EV code signing certificate

## How to Run:

### Option 1 (Easier): Using .Bat Launcher
1. Download the latest version of the script. (Direct link [here](https://github.com/Michatec/Windows-Super-god-Mode/releases/download/1.2.6/Super_God_Mode.ps1))
2. Download the launcher batch file to the same location. (Direct link [here](https://github.com/Michatec/Windows-Super-god-Mode/releases/download/1.2.6/SuperGodMode-Launcher.bat))
3. Run the batch file.

### Option 2: Manually running

1. Download the latest version of the script. (Direct link [here](https://github.com/Michatec/Windows-Super-god-Mode/releases/download/1.2.6/Super_God_Mode.ps1))
2. Open PowerShell to the directory with the script. (Tip: In File Explorer, just type "PowerShell.exe" into the address bar to open it to that path).
3. Run the following command to allow script execution temporarily for the current session. 
   ```
   Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope Process
   ```
   ^ **Note:** You might see a warning about changing the execution policy, but the `-Scope Process` part ensures that the change is only temporary, and will only apply to that specific PowerShell window, so you can choose to allow. You can read more in [this article](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-5.1#-scope). 
   
5. Run the script:
   ```
   .\Super_God_Mode.ps1
   ```
   - If no parameters are provided, a GUI will appear for easy configuration.
   - You can also run the script with optional parameters (see below).


## CLI Parameters

Note: Except for `-Debug` and `-Verbose`, you must use `-NoGUI` for arguments to take effect.

#### Alternative Options Arguments

- `-DontGroupTasks`: Prevent grouping task shortcuts by application name
- `-UseAlternativeCategoryNames`: Use alternative category names for task links
- `-AllURLProtocols`: Include third-party URL protocols from installed software
- `-DeepScanHiddenLinks`: Scans for hidden links in all files in the install directory of non-appx-package apps, otherwise only the main binary file is searched.
- `-CollectExtraURLProtocolInfo`: Collect additional information about URL protocols
- `-AllowDuplicateDeepLink`: Will not skip Deep Link shortcuts that are exactly the same as an existing task link

#### Control Output

- `-Output`: Specify a custom output folder path
- `-KeepPreviousOutputFolders`: Don't auto-delete existing output folders before running

#### Arguments to Limit Shortcut Creation

- `-NoStatistics`: Don't create statistics folder and files
- `-NoReadMe`: Don't create tips text file
- `-SkipCLSID`: Skip creating shortcuts for CLSID-based shell folders
- `-SkipNamedFolders`: Skip creating shortcuts for named special folders
- `-SkipTaskLinks`: Skip creating shortcuts for task links
- `-SkipMSSettings`: Skip creating shortcuts for ms-settings: links
- `-SkipDeepLinks`: Skip creating shortcuts for deep links
- `-SkipURLProtocols`: Skip creating shortcuts for URL protocols
- `-SkipHiddenAppLinks`: Skip creating shortcuts to hidden app links

#### Debugging

- `-Verbose`: Enable verbose output. Can be used with or without `-NoGUI`.
- `-Debug`: Enable debug output (also enables verbose output). Can be used with or without `-NoGUI`.
- `-timing`: Enable timing output to show how long each section of the script takes to run. Also enabled by verbose/debug switches.
- `-debugSkipAppxSearch`: Skip searching for hidden links in AppX packages, and only search for non-appx programs.
- `-debugSearchOnlyProtocolList`: Specify a comma-separated list of URL protocols (surrounded by quotes) to search for, and no others.
- `uniqueOutputFolder`: Append a unique identifier to the output folder name to prevent overwriting existing folders.

#### Advanced Arguments

- `-NoGUI`: Skip the GUI dialog and run with default or provided parameters
- `-CustomDLLPath`: Specify a custom DLL file path for shell32.dll
- `-CustomLanguageFolderPath`: Specify a path to a folder containing language-specific MUI files
- `-CustomSystemSettingsDLLPath`: Specify a custom path to the SystemSettings.dll file
- `-CustomAllSystemSettingsXMLPath`: Specify a custom path to the "AllSystemSettings_" XML file

### Example

```powershell
.\Super_God_Mode.ps1 -Output "C:\SuperGodMode" -AllURLProtocols -Verbose
```

## Notes

- Some shortcuts may not work on all Windows versions due to differences in available features.
- The script does not modify any system settings; it only creates shortcuts to existing Windows features.
- All parameters and GUI settings are optional. The script will run with default settings if the user doesn't change anything.

___
