# Contributing

Thanks for your interest in contributing to Matugen Theme! Here's how to get started.

## Setup

```bash
git clone https://github.com/haikalllp/vscode-matugen-theme.git
cd vscode-matugen-theme
npm install
```

## Development

```bash
npm run compile      # Compile TypeScript → out/
npm run watch        # Watch mode for development
npm run lint         # Run ESLint on src/
```

## Running the Extension

### VS Code Debug (recommended)

1. Open the project in VS Code
2. Press **F5** — this opens an Extension Development Host with the extension loaded
3. Make sure [matugen](https://github.com/InioX/matugen) is installed and configured (see [README](./README.md))
4. Run `matugen` to generate colors — the theme will auto-update

### Command Line

```bash
npm run compile
code --extensionDevelopmentPath="$PWD" .
```

### Package as VSIX

```bash
npm run compile
npx @vscode/vsce package
code --install-extension matugen-theme-*.vsix
```

## Testing

The project currently relies on manual testing via the Extension Development Host (**F5**). Before submitting a PR, please verify:

- The theme loads correctly in both light and dark modes
- `Matugen Theme: Update Theme` and `Matugen Theme: Clear Cache` commands work
- Running `matugen` will trigger an automatic theme update

## Pull Requests

1. Create a feature branch
2. Make your changes
3. Run `npm run lint` and fix any issues
4. Open a PR with a clear description of your changes
