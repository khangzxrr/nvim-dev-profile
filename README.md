# nvim-dev-profile

My personal Neovim setup for full-stack TypeScript and Java development, built on the [LazyVim](https://github.com/LazyVim/LazyVim) starter.

![Neovim](https://img.shields.io/badge/Neovim-LazyVim-57A143?logo=neovim&logoColor=white)
![Lua](https://img.shields.io/badge/Lua-2C2D72?logo=lua&logoColor=white)

## Overview

This config uses LazyVim's defaults, the plugin manager [lazy.nvim](https://github.com/folke/lazy.nvim), and a few extras and overrides for day-to-day TypeScript/Node.js and Java work. It includes debugging, formatting and linting.

## What's included

### LazyVim extras (`lazyvim.json`)

- `lang.typescript`, `lang.java` (nvim-jdtls), `lang.json`
- `dap.core`: debugging with nvim-dap and nvim-dap-ui
- `formatting.prettier`, `linting.eslint`
- `coding.mini-surround`, `util.mini-hipatterns`

### Custom plugin specs (`lua/plugins/`)

| File | What it does |
| --- | --- |
| `colorscheme.lua` / `tokyonight.lua` | Tokyonight *moon* theme with transparent background, sidebars and floats |
| `dap-typescript.lua` | `pwa-node` debug adapter for TypeScript with **Launch file** and **Attach to process** configurations, and installs `js-debug-adapter` through Mason |
| `disable-mason-dap.lua` | Turns off `mason-nvim-dap` so the manual adapter config above is used |
| `nvim-cmp.lua` | Turns off automatic completion popups (open them manually) |
| `notify.lua` | nvim-notify stacks notifications bottom-up |
| `hardtime.lua` | [hardtime.nvim](https://github.com/m4xshen/hardtime.nvim) to build better Vim motion habits |
| `example.lua` | LazyVim's example spec (turned off) |

Plugin versions are pinned in `lazy-lock.json`.

## Installation

Requires Neovim 0.9+, Git, Node.js (for the TypeScript tooling and debugger), a Nerd Font, and a JDK if you use the Java extra.

```bash
# back up your current config
mv ~/.config/nvim ~/.config/nvim.bak
mv ~/.local/share/nvim ~/.local/share/nvim.bak

# clone
git clone https://github.com/khangzxrr/nvim-dev-profile ~/.config/nvim

# start Neovim; lazy.nvim bootstraps itself and installs plugins
nvim
```

### TypeScript debugger path

`lua/plugins/dap-typescript.lua` expects the VS Code JS debug server at:

```
~/js-debug-dap-v1.77.0/js-debug/src/dapDebugServer.js
```

Download [vscode-js-debug](https://github.com/microsoft/vscode-js-debug/releases) there, or update the path in that file.

## Structure

```
.
├── init.lua              # bootstraps config.lazy
├── lazyvim.json          # enabled LazyVim extras
├── lazy-lock.json        # pinned plugin versions
└── lua/
    ├── config/           # lazy.lua, options, keymaps, autocmds
    └── plugins/          # custom plugin specs / overrides
```

See the [LazyVim documentation](https://lazyvim.github.io/installation) for default keymaps and more customization.

## License

[Apache 2.0](LICENSE), inherited from the LazyVim starter template.
