# Contributing

## Build

```bash
npm install          # Install dependencies
npm run compile      # Compile TypeScript → out/
npm run watch        # Compile in watch mode during development
```

## Run

### Option A: VS Code Run and Debug

1. Open this project folder in VS Code
2. Press **F5** (or go to **Run → Start Debugging**) — this opens a new VS Code Extension Development Host window with the extension loaded
3. Make sure you have [matugen](https://github.com/InioX/matugen) installed and configured (see [README](./README.md)), then run `matugen` to generate colors
4. The theme auto-updates when matugen colors change

### Option B: Command Line

```bash
npm run compile
code --extensionDevelopmentPath="$PWD" .
```

Or package and install manually:

```bash
npm run compile
npx @vscode/vsce package
code --install-extension matugen-theme-*.vsix
```

## Lint

```bash
npm run lint         # Run ESLint on src/
```

## Test

There are no dedicated test scripts defined beyond `npm run pretest` (which just compiles). The project relies on manual testing via the Extension Development Host (**F5**).
