# Prism / custom llama.cpp backend (cybort fork)

Upstream: https://github.com/lmstudio-ai/lmstudio-js (CLI submodule: `lmstudio-ai/lms`).

## Extra command

```text
lms runtime register-custom --config <lmstudio-prism/config.json>
lms runtime register-custom --path <prism-cuda-dir> --prism-root <lmstudio-prism>
lms runtime register-custom --url <zip-url> --force
```

Shells to [lmstudio-prism](../lmstudio-prism) (`install.py` / `install.ps1`).

Default prism config uses `install_target=overlay` (Prism binaries inside the donor CUDA12 backend so `lms runtime ls` keeps listing it).

## Build (verified on Windows Node v26)

```powershell
npm install
npx turbo run build --filter=@lmstudio/lms-cli...
cd publish/cli
$env:LMS_NO_SIGN = "true"
npm run build   # produces dist/index.js (make-bin needs DigiCert smctl; skip with LMS_NO_SIGN for exe)
node dist/index.js runtime register-custom --help
node dist/index.js runtime register-custom --path K:\project\Strata\third_party\prism-llama\cuda --prism-root K:\project\lmstudio-prism
```

Without a full monorepo build:

```powershell
python K:\project\lmstudio-prism\install.py --config K:\project\lmstudio-prism\config.json --force
```
