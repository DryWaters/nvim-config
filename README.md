# Neovim configuration

Personal Neovim configuration based on
[kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim).

## Requirements

- Neovim 0.12 or newer
- [Tree-sitter CLI](https://github.com/tree-sitter/tree-sitter) 0.26.1 or newer
- Git, Make, a C compiler, and [ripgrep](https://github.com/BurntSushi/ripgrep)
- `curl` and `tar` for nvim-treesitter parser installation
- A [Nerd Font](https://www.nerdfonts.com/font-downloads)
- [LazyGit](https://github.com/jesseduffield/lazygit) for the LazyGit integration
- [Delve](https://github.com/go-delve/delve) for Go debugging
- `gofmt` and [goimports](https://pkg.go.dev/golang.org/x/tools/cmd/goimports) for Go formatting
- [vscode-js-debug](https://github.com/microsoft/vscode-js-debug) for JavaScript debugging
- [Delta](https://github.com/dandavison/delta) for Telescope Undo diffs

## Notable plugins

The configuration includes kickstart.nvim's core plugins and enabled optional
modules (the lint module remains disabled), plus:

- [Telescope Undo](https://github.com/debugloop/telescope-undo.nvim)
- [LazyGit](https://github.com/kdheepak/lazygit.nvim)
- [nvim-dap-vscode-js](https://github.com/mxsdev/nvim-dap-vscode-js)
- [Neotest](https://github.com/nvim-neotest/neotest) with Jest and Go adapters
- [Harpoon](https://github.com/ThePrimeagen/harpoon)
- [nvim-notify](https://github.com/rcarriga/nvim-notify)
- [Persistence](https://github.com/folke/persistence.nvim)
- [Trouble](https://github.com/folke/trouble.nvim)

Telescope tracks `master`. nvim-treesitter tracks `main`, installs parsers under
Neovim's data directory, and uses Neovim's built-in Treesitter highlighting API.

## Keybindings

`<leader>` is Space. Built-in mappings are discoverable with `<leader>sk`.

- `<leader>0` opens the Harpoon menu; `<leader>a` adds a file; `<leader>1` through
  `<leader>9` select Harpoon entries.
- `<leader>lg` opens LazyGit.
- `<leader>tr` runs tests; the other `<leader>t` mappings stop tests, open output,
  show the summary, debug, or toggle watch mode.
- `<leader>qs`, `<leader>ql`, `<leader>qS`, and `<leader>qd` restore, select, or
  stop Persistence sessions.
- `<leader>xx`, `<leader>xX`, `<leader>xq`, `<leader>cs`, and `<leader>cl` open
  Trouble diagnostics, quickfix, symbols, and LSP views.
- `<leader>s` contains Telescope search mappings; `<leader>u` opens Telescope Undo.
- `<F1>`, `<F2>`, `<F3>`, `<F5>`, `<F7>`, `<leader>b`, and `<leader>B` control debugging.

## Runtime state

lazy.nvim plugins, Treesitter parsers, Mason tools, caches, logs, undo history,
session data, and other runtime state live under Neovim's standard data, state,
and cache directories. `lazy-lock.json` is intentionally ignored, so plugin locks
and generated/runtime files must not be committed to this repository.

## Startup troubleshooting

If Neovim starts from a directory that has been deleted, the configuration
silently recovers to a valid `$HOME`, then falls back to Neovim's config
directory. A valid working directory is left unchanged. Startup stops with a
clear error if neither fallback directory is available.
