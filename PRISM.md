# Prism / custom llama.cpp backend (cybort fork)

Upstream: https://github.com/lmstudio-ai/lmstudio-js (CLI submodule: `lmstudio-ai/lms`).

## Extra command

```text
lms runtime register-custom --config <lmstudio-prism/config.json>
lms runtime register-custom --path <prism-cuda-dir> --prism-root <lmstudio-prism>
lms runtime register-custom --url <zip-url> --force
```

This shells to [`lmstudio-prism`](../lmstudio-prism) (`install.py` / `install.ps1`), which overlays Prism
binaries onto an LM Studio donor backend under `~/.lmstudio/extensions/backends/`.

Desktop UI still uses **Ctrl+Shift+R** (or `lms runtime select`) to activate the installed backend.

## Build

Same as upstream (needs Node ^25.5):

```powershell
npm install
npm run make-cli
node publish/cli/dist/index.js runtime register-custom --help
```

Without a full monorepo build, run the installer directly:

```powershell
python K:\project\lmstudio-prism\install.py --config K:\project\lmstudio-prism\config.json --force
```
