# Unity System Tray
A simple script that adds a system tray (notification) icon for Unity applications. [Forked!](https://github.com/Haoming02/unity-system-tray)

> [!Important]
> Since the script uses functions from `user32.dll`, it is only usable on **Windows** systems

## Features

- ✅ **System Tray Icon** with custom texture and tooltip
- ✅ **Context Menu** with support for multi-level submenus
- ✅ **Left-click and Right-click** actions
- ✅ **Balloon tip notifications**
- ✅ **IL2CPP compatibility**
- ✅ **Multi-level menu support** using `\` separator

## How to Use

- Call the `TrayIcon.Init` function:
    - **appName:** Just an internal `string`, will not be visible
    - **tooltip:** Shows up when you hover the icon
    - **iconTexture:** Icon texture
    - **actions:** A `List` of `string`, `Action` pairs
        - For regular strings, it will be shown as an option in the menu when right-clicking the icon
        - Use `TrayIcon.LEFT_CLICK` for when left-clicking the icon directly
        - Use `TrayIcon.SEPARATOR` to add a divider in the menu
        - Use `\` to create multi-level submenus (e.g., "File\\Open")

- Call `TrayIcon.ShowBalloonTip` to trigger a notification

### Example
```csharp
TrayIcon.Init(
    "MyApp",
    "My Unity Application",
    iconTexture,
    new List<(string, Action)>()
    {
        (TrayIcon.LEFT_CLICK, OnLeftClick),
        ("Show Message", ShowMessage),
        (TrayIcon.SEPARATOR, null),
        ("File\\Open", OpenFile),
        ("File\\Save", SaveFile),
        ("Exit", ExitApp)
    }
);
