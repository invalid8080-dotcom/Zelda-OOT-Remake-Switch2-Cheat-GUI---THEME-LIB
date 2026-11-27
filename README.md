

# Zelda-OOT-Remake-Switch2-Cheat-GUI---THEME-LIB
the repo houses themes for the zelda OOT cheat gui, users can download themes in the cheat gui it self via the settings tab


Maintained by **a_cow_says**

- [Main Cheat GUI repository](https://github.com/invalid8080-dotcom/Zelda-OOT-Remake-Switch-2---Cheat-GUI)
- [Theme releases](https://github.com/invalid8080-dotcom/Zelda-OOT-Remake-Switch2-Cheat-GUI---THEME-LIB/releases)
- [Issues and suggestions](https://github.com/invalid8080-dotcom/Zelda-OOT-Remake-Switch2-Cheat-GUI---THEME-LIB/issues)

## About

Starting with v1.3.1, the Cheat GUI is planned to support independently developed themes through an integrated Theme Manager.

Themes will be stored locally and managed separately from the Cheat GUI itself, allowing users to update, replace or create themes without recompiling the application.

Support for historical GUI builds is also planned.


<img width="1409" height="847" alt="ChatGPT_PqnLQNj4GQ" src="https://github.com/user-attachments/assets/474d476f-ea12-4544-b94e-a78ecb60efc7" />

<img width="1536" height="1024" alt="Four Themed Cheat GUI Screenshots-1" src="https://github.com/user-attachments/assets/0c5e3686-f157-4048-8228-7ff1f06b4200" />

## Theme Manager

The Theme Manager will consist of two tabs.

### Browser

Displays themes published through this repository.

- Theme descriptions and version information.
- Animated GIF and static PNG previews.
- Theme installation and updates.
- Search, sorting and grid/list views.

### Installed

Displays themes available locally.

- Apply or switch themes.
- Update installed themes.
- Uninstall custom themes.
- Restore the original GUI appearance.
- Open the local themes directory.

Installed themes will remain usable without an internet connection.

## Supported customization

The theme engine is being designed to support the following components:

| Component | Customization |
|---|---|
| Buttons | Textures, colours and interaction states |
| Tags | Status indicators and borders |
| Tabs | Backgrounds, icons and selection indicators |
| Tiles | Backgrounds, borders and spacing |
| Blocks | Section styling |
| Fonts | Font families, weights and sizes |
| Icons | Custom interface icons |
| Cursors | Custom mouse cursors |
| Backgrounds | Static and animated assets |
| Overlays | Decorative elements |
| Sounds | Event-based sound effects |
| Animations | Interface transitions |
| Transparency | Window and tile opacity |
| Effects | Blur and other supported visual effects |
| Languages | JSON-based translations |

Themes will not modify the underlying cheat functionality.

## Directory structure

Themes will be stored relative to the Cheat GUI executable.

```text
Cheat GUI/
├── CheatGUI.exe
├── config/
│   ├── settings.ini
│   └── theme_settings.json
├── theme_engine/
│   ├── compatibility/
│   ├── defaults/
│   └── engine_manifest.json
└── themes/
    ├── Default/
    ├── Phantom_Glass/
    ├── _cache/
    └── _downloads/
```

The `themes/` directory and theme preferences are intended to persist across GUI updates and supported version rollbacks.

## Creating a theme

The following is the proposed theme package structure.

```text
Example_Theme/
├── theme.json
├── styles.qss
├── colors.json
├── layout.json
├── preview.gif
├── preview.png
├── languages/
│   ├── en.json
│   ├── fr.json
│   ├── zh-CN.json
│   └── zh-TW.json
├── buttons/
├── tags/
├── fonts/
├── overlays/
├── tabs/
├── tiles/
├── blocks/
├── cursors/
├── backgrounds/
├── icons/
├── sounds/
├── animations/
└── effects/
```

Not all directories or assets are required.

Missing optional assets will inherit the corresponding default GUI styling. A simple theme may only require a manifest and stylesheet.

### Theme manifest

`theme.json` identifies the theme, its version, available assets and supported features.

Example:

```json
{
    "id": "phantom_glass",
    "name": "Phantom Glass",
    "author": "a_cow_says",
    "version": "1.0.0",
    "theme_api": 1,
    "description": "Transparent desktop theme.",
    "stylesheet": "styles.qss",
    "preview": {
        "gif": "preview.gif",
        "png": "preview.png"
    },
    "localization": {
        "enabled": true,
        "directory": "languages/",
        "default_language": "en",
        "supported_languages": [
            "en",
            "fr",
            "zh-CN"
        ]
    },
    "features": {
        "transparency": true,
        "background_blur": true,
        "animations": true,
        "custom_fonts": true,
        "custom_sounds": true,
        "custom_cursors": true
    }
}
```

The manifest specification is preliminary and may change during development.

### Preview files

Theme previews will use the following priority:

1. `preview.gif`
2. `preview.png`
3. Default placeholder

Animated previews will loop directly inside the Theme Manager.

### Localization

Themes can include their own translations through UTF-8 encoded JSON files in the `languages/` directory.

The selected GUI language determines which translation file is loaded.

| Language | Filename |
|---|---|
| English | `en.json` |
| French | `fr.json` |
| Simplified Chinese | `zh-CN.json` |
| Traditional Chinese | `zh-TW.json` |
| Japanese | `ja.json` |
| Korean | `ko.json` |
| German | `de.json` |
| Spanish | `es.json` |
| Brazilian Portuguese | `pt-BR.json` |
| Russian | `ru.json` |

Additional languages can be provided by theme creators.

#### English

`languages/en.json`

```json
{
    "theme.name": "Phantom Glass",
    "theme.description": "Transparent desktop theme.",
    "theme.settings.window_opacity": "Window Opacity",
    "theme.settings.tile_opacity": "Tile Opacity",
    "theme.settings.background_blur": "Background Blur",
    "theme.settings.always_on_top": "Always on Top"
}
```

#### Simplified Chinese

`languages/zh-CN.json`

```json
{
    "theme.name": "幻影玻璃",
    "theme.description": "透明桌面主题。",
    "theme.settings.window_opacity": "窗口不透明度",
    "theme.settings.tile_opacity": "卡片不透明度",
    "theme.settings.background_blur": "背景模糊",
    "theme.settings.always_on_top": "窗口置顶"
}
```

#### French

`languages/fr.json`

```json
{
    "theme.name": "Verre Fantôme",
    "theme.description": "Thème de bureau transparent.",
    "theme.settings.window_opacity": "Opacité de la fenêtre",
    "theme.settings.tile_opacity": "Opacité des tuiles",
    "theme.settings.background_blur": "Flou d'arrière-plan",
    "theme.settings.always_on_top": "Toujours au premier plan"
}
```

Missing translation keys will fall back to the theme's default language, followed by embedded default text.

Changing themes will not change the selected GUI language.

Changing languages will not reset the active theme.

Existing cheat names, descriptions and status messages remain managed by the Cheat GUI's own translation system.

### Fonts

Custom fonts can be included in the `fonts/` directory.

If a custom font does not contain the characters required by the selected language, the GUI will use an appropriate fallback font.

Themes should account for differences in translated text length and right-to-left languages.

### Sound effects

Optional sound assets can be included in the `sounds/` directory.

Planned events include:

- Button hover and click.
- Tab switching.
- Cheat activation and deactivation.
- Emulator connection and disconnection.
- Notifications and errors.
- Theme installation and switching.

Sound effects can be disabled independently of the active theme.

## Theme releases

Themes will use independent version numbers.

Proposed release naming convention:

```text
phantom_glass_v1.0.0
```

Release assets:

```text
phantom_glass_v1.0.0.zip
preview.gif
preview.png
```

Release descriptions should include compatibility information, supported languages, author credits and any known issues.

## Version compatibility

| GUI version | Theme support target |
|---|---|
| v1.0 | Legacy compatibility |
| v1.1.x | Legacy compatibility |
| v1.2.x | Legacy compatibility |
| v1.3.0 | Legacy compatibility |
| v1.3.1 | Native |
| Future releases | Native |

Historical compatibility is not yet verified. Older versions may require compatibility-enabled rebuilds.

Unsupported theme components should fall back to default styling without affecting the functionality of the historical build.

## Default theme

The original Cheat GUI appearance will remain available as the Default Theme.

It cannot be uninstalled.

If a custom theme fails to load, the GUI will fall back to its original appearance.

## Package restrictions

Theme packages are intended to contain configuration files and visual or audio assets only.

Executable files, DLLs and scripts are not part of the supported theme format.

Theme packages will not have access to game memory, GDB communication, cheat logic or game saves.

## Contributing

Community themes, translations and suggestions are welcome.

Theme submission instructions will be added once the theme engine and package specification are finalized.

Please ensure that contributed assets are authorized for redistribution.

## Development status

- [x] Theme Manager design
- [x] Theme directory architecture
- [x] Theme package specification draft
- [x] Multilingual JSON specification
- [x] Historical compatibility planning
- [ ] Theme engine implementation
- [ ] GitHub integration
- [ ] Theme installation and updates
- [ ] Legacy compatibility testing
- [ ] Official theme releases

## Disclaimer

This is an independent community project and is not affiliated with Nintendo.

This repository is intended for Cheat GUI themes and associated assets. No game files, firmware, encryption keys or emulators are distributed here.

