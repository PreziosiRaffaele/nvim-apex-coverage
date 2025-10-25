# nvim-apex-coverage

[![Lua](https://img.shields.io/badge/Lua-blue.svg?style=flat-square&logo=lua)](https://www.lua.org)
[![Neovim >= 0.10](https://img.shields.io/badge/Neovim-%3E%3D%200.10-blueviolet.svg?style=flat-square)](https://neovim.io/)

A Neovim plugin to fetch and display Salesforce Apex code coverage directly within the editor. It utilizes the `sf` CLI to query coverage data and visualizes it using Neovim's sign column.

## Demo
<!-- Demo source: https://github.com/nvim-mini/assets/blob/main/demo/demo-pick.mp4 -->
https://github.com/user-attachments/assets/7ddd79df-e5fa-4e7c-8a2f-e1c83b3fd7ab

## ✨ Features

*   Fetches Apex code coverage data using the Salesforce CLI (`sf`).
*   Displays total aggregated coverage for a class/trigger.
*   Displays coverage specific to individual test methods.
*   Visualizes covered and uncovered lines using signs.
*   Provides an option to refresh coverage data. 
*   Configurable key mappings.

## 📋 Requirements

*   [Neovim](https://neovim.io/) >= 0.10 (uses `vim.system` for async)
*   [Salesforce CLI (`sf`)](https://developer.salesforce.com/tools/sfdxcli) installed and authenticated to a target org.

## 📦 Installation

Using [lazy.nvim](https://github.com/folke/lazy.nvim):

```lua
-- Add to your lazy.nvim plugin configuration
return {
    "PreziosiRaffaele/nvim-apex-coverage",
    keys = {
        { "<leader>ac", "<cmd>ApexCoverage<cr>", desc = "Apex Coverage" },
        { "<leader>aC", "<cmd>ApexCoverageClean<cr>", desc = "Clean Apex Coverage" },
    },
}
```

## 🚀 Usage

1.  Open an Apex class (`.cls`) or trigger (`.trigger`) file in Neovim.
2.  Run the `:ApexCoverage` command or the keymap you configured during setup.
3.  A selection menu will appear:
    *   **Total Coverage:** Shows aggregated coverage for the entire file.
    *   **[TestClass.TestMethod] - XX.XX%:** Shows coverage specific to that test method.
    *   **Refresh Data:** Fetches the latest coverage data from Salesforce.
4.  Select an option to visualize the coverage:
    *   Covered lines will be marked with a sign (default: `▎` with `DiffAdd` highlight).
    *   Uncovered lines will be marked with a sign (default: `▎` with `DiffDelete` highlight).
5.  To clear the coverage signs, run the `:ApexCoverageClean` command or the keymap you set for it.

## ⌨️ Commands

*   `:ApexCoverage`: Fetches coverage data (if not cached) for the current Apex file and displays the selection menu to visualize coverage.
*   `:ApexCoverageClean`: Removes all coverage signs placed by this plugin from the current buffer.

## 🎯 Scope & Related Plugins

This plugin is specifically designed to **fetch and visualize Apex code coverage**. It does not include functionality for running Apex tests or other general interactions with the Salesforce CLI.

For a more comprehensive Salesforce development experience within Neovim, including running tests, deploying and retrieving metadata, and more, check out:

*   [xixiaofinland/sf.nvim](https://github.com/xixiaofinland/sf.nvim)
