# cursor-windsurf-convert ("cuws")

*Surf your AI rules from **Cursor** to **Windsurf** (and back) faster than you can say `cat | cuws`.* 🏄‍♂️⛵

[![CI](https://github.com/gmickel/cursor-windsurf-convert/actions/workflows/ci.yml/badge.svg)](https://github.com/YOUR_ORG/cursor-windsurf-convert/actions/workflows/ci.yml)
[![License](https://img.shields.io/github/license/gmickel/cursor-windsurf-convert)](LICENSE)
[![NPM Version](https://img.shields.io/npm/v/cursor-windsurf-convert)](https://www.npmjs.com/package/cursor-windsurf-convert)
[![NPM Downloads](https://img.shields.io/npm/dw/cursor-windsurf-convert)](https://www.npmjs.com/package/cursor-windsurf-convert)

[About](#-about) •
[Why cuws?](#-why-cuws) •
[Key Features](#-key-features) •
[Quick Start](#-quick-start) •
[Installation](#-installation) •
[Usage](#-usage) •
[API](#-api) •
[Developing](#-developing) •
[Contributing](#-contributing) •
[Roadmap](#-roadmap) •
[FAQ](#-faq)

---

## 📖 About

`cuws` is a tiny but mighty Node.js CLI + library that losslessly converts rule files between **Cursor** (`.cursor/rules/*.mdc`) and **Windsurf** (`.windsurf/rules/*.md`) formats.  Pipe it, script it, or call it from TypeScript—either way your rules arrive on the right shore untouched.

> *Windsurf shipped file‑based rules on **7 May 2025**. This project exists so you can ride that wave **today**.*

---

## 🤔 Why cuws?

* **Zero friction** – stream via `stdin`/`stdout` or give it paths.
* **Bidirectional** – Cursor ➜ Windsurf **and** Windsurf ➜ Cursor.
* **Fast** – converts a 1 kB rule in < 50 ms. Blink and you’ll miss it.
* **Lossless metadata mapping** – front‑matter stays intact, content unchanged.
* **CI‑ready** – deterministic, non‑interactive, exit codes you can trust.
* **Tiny footprint** – minimal runtime dependencies (`gray-matter`, `commander`, `fast-glob` for CLI).

---

## ✨ Key Features

| Feature                         | Description                                                                         |
| ------------------------------- | ----------------------------------------------------------------------------------- |
| 🔄 **Bidirectional conversion** | `cuws` detects the source format or let you force it.                               |
| 📂 **Directory mode**           | Convert whole trees while mirroring structure (requires output directory specified). |
| 🏗️ **TypeScript API**          | Import `convertString()`, `convertFile()`, or `convertDirectory()` in your scripts. |
| 🪝 **Streaming first**          | Works perfectly in Unix pipes & GitHub Actions.                                     |
| 🐚 **Single‑file binary**       | ES module with hashbang—no compilation required.                                    |

---

## 🚀 Quick Start

```bash
# Global install
npm install -g cursor-windsurf-convert

# Convert a single file (Cursor ➜ Windsurf)
cuws -i .cursor/rules/auth.mdc -o .windsurf/rules/auth.md

# Pipe via stdin/stdout
git show HEAD:my-rule.mdc | cuws --reverse > my-rule-cursor.mdc

# Batch convert an entire repo (dry‑run first, output to 'converted-rules' directory)
cuws -d . -o ./converted-rules --reverse --dry-run
```

---

## 📦 Installation

```bash
# Use npx (no install)
npx cursor-windsurf-convert --help

# Or add as a dev dependency
yarn add -D cursor-windsurf-convert # or npm i -D ...
```

> **Node ≥ 18** required (tested on 18 & 20).

---

## 💻 Usage

### CLI

```bash
cuws [options]
```

| Flag                  | Default     | Description                                                                 |
| --------------------- | ----------- | --------------------------------------------------------------------------- |
| `-i, --input <path>`  | `-`         | Path to source file or `-` for stdin. Conflicts with `-d`.                  |
| `-o, --output <path>` | `-`         | Path to dest file (with `-i`) or output directory (required with `-d`).     |
| `-r, --reverse`       | `false`     | Convert from Windsurf (.md) to Cursor (.mdc).                               |
| `--force <format>`    |             | Override auto-detection (`cursor` or `windsurf`).                           |
| `-d, --dir <path>`    |             | Recursively convert directory. Requires `-o` for output. Conflicts with `-i`. |
| `--dry-run`           | `false`     | Print planned actions, don’t write files.                                   |
| `--verbose`           | `false`     | Extra logging.                                                              |

### Programmatic API

```typescript
import {
  convertString,
  convertFile,
  convertDirectory,
} from 'cursor-windsurf-convert';

// Convert a string
const cursorRuleContent = '...'; // content of a .mdc file
const windsurfRuleContent = convertString(cursorRuleContent, 'cw');

// Convert a single file
async function exampleConvertFile() {
  const outputPath = await convertFile('path/to/source.mdc', 'path/to/output.md');
  console.log(`Converted file written to: ${outputPath}`);
}

// Convert a directory
async function exampleConvertDirectory() {
  const results = await convertDirectory('path/to/source-dir', 'path/to/output-dir');
  results.forEach(result => {
    console.log(`${result.sourcePath} -> ${result.destinationPath} (${result.status})`);
  });
}
```

See [API docs](docs/API.md) for full typings.

---

## 🛠️ Developing

1. Clone & install deps:

   ```bash
   git clone https://github.com/YOUR_ORG/cursor-windsurf-convert.git
   cd cursor-windsurf-convert && pnpm install
   ```
2. Link the CLI for local testing:

   ```bash
   pnpm run build # if you transpile
   pnpm link --global   # exposes `cuws` in PATH
   ```
3. Run tests:

   ```bash
   pnpm test
   ```

### `package.json` bin field

```jsonc
{
  "name": "cursor-windsurf-convert",
  "version": "1.0.0",
  "bin": {
    "cuws": "dist/cli.mjs"
  },
  ...
}
```

The CLI file **must** start with `#!/usr/bin/env node` and be `chmod +x`.

---

## 🤝 Contributing

PRs welcome! Check the [open issues](https://github.com/gmickel/cursor-windsurf-convert/issues) or open a new one. Also see [CONTRIBUTING.md](CONTRIBUTING.md) for details.

---

## 🏄 Roadmap

* [x] One‑file conversion
* [x] Directory batch mode

---

## ❓ FAQ

| Q                                  | A                                              |
| ---------------------------------- | ---------------------------------------------- |
| *Does it change my markdown body?* | Nope. Only the YAML/MD header is mapped.       |
| *Can I embed this in my own tool?* | Absolutely—import the TS API.                  |

---

## 📄 License

[MIT](LICENSE) © 2025 Gordon Mickel

---

⭐ **If this saves you time, drop a star!** ⭐
