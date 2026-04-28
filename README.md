<div align="center">

# Matugen Theme

Visual Studio Code theme that syncs with your wallpaper palette in real time using matugen.

[![](https://img.shields.io/github/last-commit/haikalllp/vscode-matugen-theme?&style=for-the-badge&color=F38D89&logo=git&logoColor=D9E0EE&labelColor=1E202B)](https://github.com/haikalllp/vscode-matugen-theme/commit/main)
[![](https://img.shields.io/badge/Matugen-Repo-F38D89?style=for-the-badge&logo=github&logoColor=D9E0EE&labelColor=1E202B)](https://github.com/InioX/matugen)
[![](https://img.shields.io/visual-studio-marketplace/v/haikalllp.matugen-theme?style=for-the-badge&color=E8857F&logo=visual-studio-code&logoColor=D9E0EE&labelColor=1E202B&label=VS%20Marketplace)](https://marketplace.visualstudio.com/items?itemName=haikalllp.matugen-theme)
[![](https://img.shields.io/open-vsx/v/haikalllp/matugen-theme?style=for-the-badge&color=F5A29F&logo=eclipse-ide&logoColor=D9E0EE&labelColor=1E202B&label=Open%20VSX)](https://open-vsx.org/extension/haikalllp/matugen-theme)
[![](https://img.shields.io/visual-studio-marketplace/d/haikalllp.matugen-theme?style=for-the-badge&color=E8857F&logo=visual-studio-code&logoColor=D9E0EE&labelColor=1E202B)](https://marketplace.visualstudio.com/items?itemName=haikalllp.matugen-theme)
[![](https://img.shields.io/github/license/haikalllp/vscode-matugen-theme?style=for-the-badge&color=F5A29F&logoColor=D9E0EE&labelColor=1E202B)](https://github.com/haikalllp/vscode-matugen-theme/blob/master/LICENSE)

## Preview

![image1](https://github.com/user-attachments/assets/0f648de2-88b6-4b2c-885b-38f0ab909f88)
![image2](https://github.com/user-attachments/assets/8e847b42-f442-4953-8c3c-9dc618a72e7a)
![image3](https://github.com/user-attachments/assets/e3e78135-7bf6-4413-b729-e73a08e9ff53)
![image4](https://github.com/user-attachments/assets/53b5ad1f-c610-4e20-bedd-b69280494042).

</div>

## Features

- Real-time color updates synced from your wallpaper palette
- Automatic light/dark detection based on background luminance
- Two theme variants: borderless and bordered
- Zero configuration, works out of the box

## Requirements

1. Install [matugen](https://github.com/InioX/matugen)

2. Copy these templates to your matugen templates folder at `~/.config/matugen/templates`:

   <details>
   <summary><code>vscode-colors</code></summary>

   ```
   {{ colors.background.default.hex }}
   {{ colors.error.default.hex }}
   {{ colors.secondary.default.hex | saturate: 20.0, hsl }}
   {{ colors.tertiary.default.hex | saturate: 15.0, hsl }}
   {{ colors.primary.default.hex }}
   {{ colors.tertiary.default.hex }}
   {{ colors.secondary_container.default.hex | saturate: 20.0, hsl }}
   {{ colors.on_surface_variant.default.hex }}
   {{ colors.surface_variant.default.hex }}
   {{ colors.error.default.hex | auto_lightness: 10.0 }}
   {{ colors.secondary.default.hex | auto_lightness: 10.0 | saturate: 20.0, hsl }}
   {{ colors.tertiary.default.hex | auto_lightness: 10.0 | saturate: 15.0, hsl }}
   {{ colors.primary.default.hex | auto_lightness: 10.0 }}
   {{ colors.tertiary.default.hex | auto_lightness: 10.0 }}
   {{ colors.primary_container.default.hex | saturate: 10.0, hsl }}
   {{ colors.on_background.default.hex }}
   ```

   </details>

   <details>
   <summary><code>vscode-colors.json</code></summary>

   ```json
   {
     "checksum": ":)",
     "wallpaper": "{{ image }}",
     "alpha": "100",
     "special": {
       "background": "{{ colors.background.default.hex }}",
       "foreground": "{{ colors.on_background.default.hex }}",
       "cursor": "{{ colors.primary.default.hex }}"
     },
     "colors": {
       "color0": "{{ colors.background.default.hex }}",
       "color1": "{{ colors.error.default.hex }}",
       "color2": "{{ colors.secondary.default.hex | saturate: 20.0, hsl }}",
       "color3": "{{ colors.tertiary.default.hex | saturate: 15.0, hsl }}",
       "color4": "{{ colors.primary.default.hex }}",
       "color5": "{{ colors.tertiary.default.hex }}",
       "color6": "{{ colors.secondary_container.default.hex | saturate: 20.0, hsl }}",
       "color7": "{{ colors.on_surface_variant.default.hex }}",
       "color8": "{{ colors.surface_variant.default.hex }}",
       "color9": "{{ colors.error.default.hex | auto_lightness: 10.0 }}",
       "color10": "{{ colors.secondary.default.hex | auto_lightness: 10.0 | saturate: 20.0, hsl }}",
       "color11": "{{ colors.tertiary.default.hex | auto_lightness: 10.0 | saturate: 15.0, hsl }}",
       "color12": "{{ colors.primary.default.hex | auto_lightness: 10.0 }}",
       "color13": "{{ colors.tertiary.default.hex | auto_lightness: 10.0 }}",
       "color14": "{{ colors.primary_container.default.hex | saturate: 10.0, hsl }}",
       "color15": "{{ colors.on_background.default.hex }}"
     }
   }
   ```

   </details>

3. Add the following to your matugen config:

   ```toml
   # VS Code matugen extension
   [templates.vscode-raw]
   input_path = './templates/vscode-colors'
   output_path = '~/.cache/matugen/vscode-colors'

   [templates.vscode-json]
   input_path = './templates/vscode-colors.json'
   output_path = '~/.cache/matugen/vscode-colors.json'
   ```

4. Run `matugen` or let it run automatically with your wallpaper manager.

## How It Works

The extension monitors `~/.cache/matugen/vscode-colors` and `~/.cache/matugen/vscode-colors.json` for changes:

1. **File Watcher:** Primary detection using chokidar with write stabilization
2. **Polling Fallback:** Secondary check every 5 seconds using hash comparison
3. **Hash-based Caching:** Themes only regenerate when the color hash changes
4. **Startup Sync:** Automatically syncs on VS Code startup if themes are outdated

## Extension Commands

| Command                       | Description                                                |
| ----------------------------- | ---------------------------------------------------------- |
| `Matugen Theme: Update Theme` | Force regenerate themes from current colors                |
| `Matugen Theme: Clear Cache`  | Clear the theme cache (forces regeneration on next change) |

## Extension Settings

| Setting                   | Default | Description                                            |
| ------------------------- | ------- | ------------------------------------------------------ |
| `matugenTheme.autoUpdate` | `true`  | Automatically update themes when matugen colors change |

## Theme Variants

- **Matugen:** Clean theme without borders (auto light/dark based on background)
- **Matugen Bordered:** Theme with subtle borders between panels (auto light/dark based on background)

## Troubleshooting

### Theme not updating automatically?

1. Check that matugen is generating files to `~/.cache/matugen/`
2. Verify the `vscode-colors` file contains colors mappings
3. Try `Matugen Theme: Clear Cache` then `Matugen Theme: Update Theme`
4. Check the Output panel (View → Output → select "Matugen Theme") for errors

### Colors look wrong?

1. Ensure your matugen templates match the ones in this repo's `examples/matugen-templates/` folder
2. The `vscode-colors.json` file is optional but provides better background/foreground colors
3. Try regenerating with `matugen`

### Extension not activating?

The extension activates after VS Code startup completes. Check:

1. Extension is enabled in the Extensions panel
2. No errors in Help → Toggle Developer Tools → Console

## Contributing

Contributions are welcome! See [CONTRIBUTING.md](./CONTRIBUTING.md) for setup and development instructions.

## Credits

- Inspired by the excellent work on [Wal Theme](https://github.com/dlasagno/vscode-wal-theme).
- Thanks to Saatvik333 for pretty much the source code [Wallust Theme](https://github.com/saatvik333/vscode-wallust-theme).
- And incredible work by InioX for [Matugen](https://github.com/InioX/matugen).

<br>

<p align="center">
  <a href="https://github.com/haikalllp/vscode-matugen-theme">
    <img src="https://img.shields.io/badge/Made%20with%20%E2%9D%A4%EF%B8%8F%20for-Matugen-F38D89?style=for-the-badge&logo=github&logoColor=D9E0EE&labelColor=1E202B" alt="Made with ❤️ for Matugen">
  </a>
</p>
